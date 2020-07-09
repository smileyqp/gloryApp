#### 1、项目初始化

```shell
//初始化项目
npx react-native init gloryApp

//开启react-native服务；此处推荐用yarn，cnpm和npm也可以
yarn start

//开启android模拟器；同react-native run-androi
npm run android 

//开启ios模拟器；同react-native run-ios
npm run ios
```

#### 2、安装`react-native-vector-icons`的icon库[链接🔗](<https://oblador.github.io/react-native-vector-icons/>)

- 添加这个库到项目中

```shell
yarn add react-native-vector-icons
```

##### IOS中配置

- 拷贝以下代码到`ios/gloryApp/Info.plist`中（注意不要放到key、value的简直对中间）

```shell
<key>UIAppFonts</key>
<array>
  <string>AntDesign.ttf</string>
  <string>Entypo.ttf</string>
  <string>EvilIcons.ttf</string>
  <string>Feather.ttf</string>
  <string>FontAwesome.ttf</string>
  <string>FontAwesome5_Brands.ttf</string>
  <string>FontAwesome5_Regular.ttf</string>
  <string>FontAwesome5_Solid.ttf</string>
  <string>Foundation.ttf</string>
  <string>Ionicons.ttf</string>
  <string>MaterialIcons.ttf</string>
  <string>MaterialCommunityIcons.ttf</string>
  <string>SimpleLineIcons.ttf</string>
  <string>Octicons.ttf</string>
  <string>Zocial.ttf</string>
  <string>Fontisto.ttf</string>
</array>
```
![](https://img-blog.csdnimg.cn/20200710021847420.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM0MjczMDU5,size_16,color_FFFFFF,t_70)

- 到`ios`目录下`pod install`安装，即可在ios中使用这个图标库

##### Android中配置

- 拷贝以下代码到`android/app/build.gradle`中,便可以使用这个库了

```shell
apply from: "../../node_modules/react-native-vector-icons/fonts.gradle"
```
![](https://img-blog.csdnimg.cn/20200710021922791.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM0MjczMDU5,size_16,color_FFFFFF,t_70)

> ⚠️注意：完成上面操作之后，需要`react-native run-ios`和`react-native run-android`重新启动两个模拟器

##### 项目中使用

[图表库链接🔗](<https://oblador.github.io/react-native-vector-icons/>)

```shell
import Ionicons from 'react-native-vector-icons/Ionicons'

<Ionicons name={'bluetooth'} size={90} style={{color:'blue'}}/>
```
![](https://img-blog.csdnimg.cn/20200710022034106.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM0MjczMDU5,size_16,color_FFFFFF,t_70)
#### 3、安装`react-navigation`库

- 安装第三方库

```shell
//安装第三方主库
yarn add react-navigation

yarn add react-navigation-stack

yarn add react-navigation-drawer

yarn add react-navigation-tabs

//安装react-native-gesture-handler依赖库
yarn add react-native-gesture-handler

//安装react-native-reanimated动画库
yarn add react-native-reanimated
```

> ⚠️注意：4.x版本开始将`createStacknavigator`、`createDrawerNavigator`、`createBottomTabNavigato`、`createTopMaterialTabNavigator`分拆到不同的库中

- `pod install`

```shell
pod install
```

- 配置`react-native-gesture-handler`

```shell
//切换到路径
cd android/app/src/main/java/com/gloryApp/

//编辑MainActivity.java,添加以下代码
import com.facebook.react.ReactActivityDelegate;
import com.facebook.react.ReactRootView;
import com.swmansion.gesturehandler.react.RNGestureHandlerEnabledRootView;

@Override
   protected ReactActivityDelegate createReactActivityDelegate() {
     return new ReactActivityDelegate(this, getMainComponentName()) {
       @Override
       protected ReactRootView createRootView() {
        return new RNGestureHandlerEnabledRootView(MainActivity.this);
       }
     };
   }
```

> ⚠️注意：完成之后重启android和ios的模拟器