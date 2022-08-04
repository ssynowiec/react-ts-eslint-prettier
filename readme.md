# react-ts-eslint-prettier

boilerplate

## how it was made

### vite 

https://vitejs.dev/guide/#scaffolding-your-first-vite-project

```
npm create vite@latest react-ts-eslint-prettier -- --template react-ts
cd react-ts-eslint-prettier
npm install
git init .
```

### eslint

https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint  
https://eslint.org/docs/latest/user-guide/getting-started  
https://github.com/iamturns/eslint-config-airbnb-typescript  

```
npm init @eslint/config

Need to install the following packages:
	@eslint/create-config
Ok to proceed? (y) y

✔ How would you like to use ESLint? · style
✔ What type of modules does your project use? · esm
✔ Which framework does your project use? · react
✔ Does your project use TypeScript? · Yes
✔ Where does your code run? · browser
✔ How would you like to define a style for your project? · guide
✔ Which style guide do you want to follow? · airbnb
✔ What format do you want your config file to be in? · JSON
✔ Would you like to install them now? · Yes
✔ Which package manager do you want to use? · npm

npm install eslint-config-airbnb-typescript --save-dev
```

.eslintrc.json

```
{
  extends: [
    'airbnb', 
+   'airbnb-typescript'
  ],
+ parserOptions: {
+   project: './tsconfig.json'
+ }
  "rules": {
+   "react/react-in-jsx-scope": "off",
+   "import/prefer-default-export": "off"
  }
}
```

package.json

```
"scripts": {
  "dev": "vite",
  "build": "tsc && vite build",
  "preview": "vite preview",
+ "lint": "eslint ./src --ext .ts,.tsx",
+ "lint:fix": "eslint ./src --ext .ts,.tsx --fix"
},
```

### prettier

https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode  
https://prettier.io/docs/en/install.html  
https://github.com/prettier/eslint-plugin-prettier  
```
npm install --save-dev --save-exact prettier
npm install --save-dev eslint-plugin-prettier eslint-config-prettier
```
.prettierrc

```
+{
+ "tabWidth": 2,
+ "semi": true,
+ "singleQuote": true,
+ "trailingComma": "all",
+ "printWidth": 80,
+ "useTabs": false,
+ "endOfLine":"auto"
+}
```

.eslintrc.json

```
"extends": [
    "plugin:react/recommended",
    "airbnb",
    "airbnb-typescript",
+   "plugin:prettier/recommended"
],

"plugins": [
    "react",
    "@typescript-eslint",
+   "prettier"
],
```

### vscode

settings.json

```
{
  ...
+ "editor.formatOnSave": true,
+ "[typescriptreact]": {
+   "editor.defaultFormatter": "esbenp.prettier-vscode"
+ }
  ...
}
```

