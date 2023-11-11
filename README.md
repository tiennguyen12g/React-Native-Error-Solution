# React-Native-Error-Solution
This repo save all my error which I catch when learning React-Native and its solution.

### 1. Error: Unable to resolve module ` react-native-screens` from `node_modules/react-navigation-/native ... "
   Related error package: "@react-navigation/native".
   ```bash
    # Solution.
     npm i react-native-screens
   ```
### 2. Invariant Violation: requireNativeComponent: "RNSScreenStackHeaderConfig" was not found in the UIManager. '@react-navigation/native-stack';
   Related error package: .
   ```bash
    # Solution.
     npm install react-native-screens react-native-safe-area-context
   ```
### 3. can not run npx react-native init MyApp --template react-native-template-typescript or TypeError: cli.init is not a function ...
   ```bash
    # Solution.
     npx react-native@latest init Name_Your_Project --template react-native-template-typescript
   ```
### 4.  Deprecated Gradle features were used in this build, making it incompatible with Gradle 9.0.
   ```bash
    # Solution 1.
     add to gradle.properties file this code below:
      org.gradle.warning.mode=all
    # Solution 2.
      step 1: npm uninstall -g react-native-cli, npm uninstall -g react-native
      step 2: npm install -g react-native-cli, npm install -g react-native 
   ```
### 5. "react-native-vector-icons" show not correct icon.
   #### Android
   *  - Edit android/app/build.gradle (NOT android/build.gradle) and add:
   ```bash
   apply from: file("../../node_modules/react-native-vector-icons/fonts.gradle")
   ```
# Tip when use package.
### 1.  when you use the '@react-navigation/native'.
   ```bash
    # You should install both packages below also.
     npm install react-native-screens react-native-safe-area-context
   ```
### 2. How to use react-navigation?
   ```bash
   Install:
   npm i @react-navigation/native @react-navigation/stack react-native-gesture-handler react-native-safe-area-context
   react-native-screens
   * Note: in App component, you should write: 
   export default function App() {
     return (
       <SafeAreaView style={{flex: 1}}>
         <AppNavigator />
       </SafeAreaView>
     );
   }
   ```
### 3. How to custom Theme with "@react-navigation/native"
* Step 1.
Create a file MyThemes.tsx like this:
```bash
import { DefaultTheme } from "@react-navigation/native";

export const customTheme = {
  ...DefaultTheme,
  colors: {
    ...DefaultTheme.colors,
    customColor: "#ccc",
  },
};
export type Theme = typeof customTheme;
```
* Step 2.
Next, create a GlobalThemes.d.ts file with the following content.
  ```bash
import type { Theme } from "./src/theme";

declare module "@react-navigation/native" {
  export function useTheme(): Theme;
}
```
* Step 3.
Use in a component
```bash
const theme = useTheme();
```
