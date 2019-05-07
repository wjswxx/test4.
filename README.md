# preference
实现设置Activity

## EditTextPreference

![](https://github.com/whiteLi12/preference/blob/master/img/1.png)

## ListPreference

![](https://github.com/whiteLi12/preference/blob/master/img/2.png)

##  跳转到另一个PreferenceScreen

![](https://github.com/whiteLi12/preference/blob/master/img/3.png)

## 启动一个网页

![](https://github.com/whiteLi12/preference/blob/master/img/4.png)

## 设置项关联，选中父选项时，子选项才显示。

![](https://github.com/whiteLi12/preference/blob/master/img/5.png)

MainActivity:
```
package com.example.myapplication;

import android.os.Bundle;

import android.preference.PreferenceActivity;

public class MainActivity extends PreferenceActivity{
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        // TODO Auto-generated method stub
        super.onCreate(savedInstanceState);
        addPreferencesFromResource(R.xml.preference);
    }

}
```

array.xml

```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <string-array name="options">
        <item>option 1</item>
        <item>option 2 </item>
        <item>option 3</item>
    </string-array>

    <string-array name="option_values" >
        <item>1</item>
        <item>2</item>
        <item>3</item>
    </string-array>
</resources>
```

preference.xml

```
<?xml version="1.0" encoding="utf-8"?>
<PreferenceScreen xmlns:android="http://schemas.android.com/apk/res/android"
    android:title="FragmentPreference">
    <PreferenceCategory
        android:title="In-line preferences"
        android:key="In-line">

        <CheckBoxPreference
            android:key="CheckBoxPreference"
            android:summary="This is a checkbox"
            android:title="CheckBox preference"
            android:defaultValue="false" />

    </PreferenceCategory>
    <PreferenceCategory
        android:title="Dialog-based preferences"
        android:key="Dialog-based">
        <EditTextPreference
            android:dialogTitle="Enter your favorite animal："
            android:key="edittextPreference"
            android:summary="An example that uses an edit text dialog"
            android:title="Edit text preference"/>
        <ListPreference
            android:key="list"
            android:title="list preference"
            android:dialogTitle="choose one"
            android:entries="@array/options"
            android:entryValues="@array/option_values"
            android:defaultValue="1" />
    </PreferenceCategory>
    <PreferenceCategory
        android:title="Launch preferences"
        android:key="Launch">
        <PreferenceScreen  xmlns:android="http://schemas.android.com/apk/res/android"
            android:key="Screen"
            android:title="Screen preference"
            android:persistent="false">
            <CheckBoxPreference
                android:key="Toggle"
                android:summary="Preference that is on the next screen but same hierarchy"
                android:title="Toggle preference"
                android:defaultValue="false" />

        </PreferenceScreen>
        <Preference android:title="Intent preference" >
            <intent android:action="android.intent.action.VIEW"
                android:data="http://www.baidu.com"
                android:summary="Launches an Activity from an Intent"/>
        </Preference>
    </PreferenceCategory>
    <PreferenceCategory
        android:title="Preferences attributes"
        android:key="attributes">
        <CheckBoxPreference
            android:key="parent"
            android:summary="This is visually a parent"
            android:title="parent checkbox preference"
            android:defaultValue="false" />
        <CheckBoxPreference
            android:dependency="parent"
            android:key="child"
            android:summary="This visually is a child"
            android:title="child checkbox preference"
            android:defaultValue="false" />
    </PreferenceCategory>
</PreferenceScreen>
```
