
# react-native-imagepicker-android

## Getting started

`$ npm install react-native-imagepicker-android --save`

### Mostly automatic installation

`$ react-native link react-native-imagepicker-android`

### Manual installation


#### Android

1. Open up `android/app/src/main/java/[...]/MainApplication.java`
  - Add `import com.sgh370.reactnative.RNImagepickerAndroidPackage;` to the imports at the top of the file
  - Add `new RNImagepickerAndroidPackage()` to the list returned by the `getPackages()` method
2. Append the following lines to `android/settings.gradle`:
  	```
  	include ':react-native-imagepicker-android'
  	project(':react-native-imagepicker-android').projectDir = new File(rootProject.projectDir, 	'../node_modules/react-native-imagepicker-android/android')
  	```
3. Insert the following lines inside the dependencies block in `android/app/build.gradle`:
  	```
      compile project(':react-native-imagepicker-android')
  	```


## Usage
```javascript
import React, {PureComponent} from 'react';
import {StyleSheet, Button, View, Image} from 'react-native';

import RNImagepickerAndroid from 'react-native-imagepicker-android';

export default class App extends PureComponent {
    
    state = {
        imageUri: null
    }

    pickImage = async () => {
        const imageSource = await RNImagepickerAndroid.pickImage();
        this.setState({
            imageUri: imageSource
        })
    }

    render() {
        return (
          <View style={styles.container}>
            <Button title="Pick Image From Gallery" onPress={this.pickImage} />
            <Image source={{uri: this.state.imageUri}} width={100} height={100} />
          </View>
        );
    }

}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#F5FCFF',
  }
});
```
  
