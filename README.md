# WaveSwipeRefreshLayout
[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-WaveSwipeRefreshLayout-brightgreen.svg?style=flat)](http://android-arsenal.com/details/1/2229)
[![Release](https://img.shields.io/github/release/recruit-lifestyle/WaveSwipeRefreshLayout.svg?label=maven version)](https://github.com/recruit-lifestyle/WaveSwipeRefreshLayout)
[![License](https://img.shields.io/hexpm/l/plug.svg)]()

This project aims to provide a reusable WaveSwipe to Refresh widget for Android.  
Even if this works fine with API.13 or less, we support only for API.14 or more.


##Screenshots
*Watch YouTube video [here](https://www.youtube.com/watch?v=aGeeLE9vxY4&feature=youtu.be).*  
![](./sc/animation.gif)  
<img src="./sc/sc1.png" width="200">
<img src="./sc/sc2.png" width="200">
<img src="./sc/sc3.png" width="200">

## Requirements
Target Sdk Version : 21  
Min Sdk Version : 14  

##How to use
1) Add this to your **build.gradle**.
```java
repositories {
    maven {
        url "https://jitpack.io"
    }
}

dependencies {
  compile 'com.github.recruit-lifestyle:WaveSwipeRefreshLayout:1.4'
}
```  

2) Add  ```java jp.co.recruit_lifestyle.android.widget.WaveSwipeRefreshLayout``` , which has at least one AbsListView, to your layout XML file.
```java
<jp.co.recruit_lifestyle.android.widget.WaveSwipeRefreshLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:id="@+id/main_swipe">

      <ListView
          android:id="@+id/main_list"
          android:layout_width="match_parent"
          android:layout_height="match_parent"/>

</jp.co.recruit_lifestyle.android.widget.WaveSwipeRefreshLayout>
```  

3) Add the function so that the your application knows when a user has completed a 'WaveSwipeRefresh'.
```java
mWaveSwipeRefreshLayout = (WaveSwipeRefreshLayout) findViewById(R.id.main_swipe);
mWaveSwipeRefreshLayout.setOnRefreshListener(new WaveSwipeRefreshLayout.OnRefreshListener() {
  @Override public void onRefresh() {
    // Do work to refresh the list here.
    new Task().execute();
  }
});

private class Task extends AsyncTask<Void, Void, String[]> {
  ...
  @Override protected void onPostExecute(String[] result) {
    // Call setRefreshing(false) when the list has been refreshed.
    mWaveSwipeRefreshLayout.setRefreshing(false);
    super.onPostExecute(result);
  }
}
```

## Credits

WaveSwipeRefresh is owned and maintained by [RECRUIT LIFESTYLE CO., LTD.](http://www.recruit-lifestyle.co.jp/)

WaveSwipeRefresh was originally created by  
[Yuki Mima](https://github.com/amyu)  
[Jumpei Matsuda](https://github.com/jmatsu)


##License

    Copyright 2015 RECRUIT LIFESTYLE CO., LTD.

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
