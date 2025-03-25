# **快适配小游戏预览插件**

## **背景**

​	为了为开发者提供无需转换即可预览WXSDK效果的支持，推出了基于`WebRTC`音视频与数据传输的`WeChat Preview`插件。

## 依赖

- **Newtonsoft Json: `3.2.1`**
- **WebRTC: `3.0.0-pre.6`**
- **Unity Render Streaming: `3.1.0-exp.7`**
- **Input System: `1.5.1`**
- **WXSDK: `v0.1.25以上`** 

## 使用方法

1. 创建Unity新项目或打开现有项目（Unity版本需>=`2020.3`）
2. `Window——Package Manager——Add package form git URL...`，输入`https://github.com/wechat-miniprogram/minigame-tuanjie-transform-sdk.git`导入微信小游戏转换插件。
3. `Window——Package Manager——Add package form git URL...`，输入`https://github.com/wechat-miniprogram/minigame-unity-wechat-preview.git`导入预览插件。
4. 可能会弹出首次使用`input system`的弹窗，点选`Yes`重启Editor。
5. 确保`Unity Editor`所在设备与预览设备处于同一局域网下（内网可能有网络限制，若无法连接可以使用移动热点）。
6. 打开`微信小游戏——在微信中预览`，并按需配置选项。
7. 点击`开始运行`，而后使用微信开发者工具打开点击出现的按钮`打开本地预览包位置`所打开的文件夹（appid为自配置）或直接使用手机扫描出现的小程序码（appid为快适配示例）即可预览。

## 预览选项

1. 本地预览包选项

   - APPID：生成的本地预览包所使用的APPID。

   - 导出路径：本地预览包的生成位置。
2. 视频选项

   - 预览方向：默认为`Portrait`。`Portrait`为竖屏预览，`Landscape`为横屏预览。

   - 帧率：默认最大帧率30帧。

   - 视频码率：默认为0～10000kbits/sec。最小/最大值范围为0～10000kbits/sec。

   - 分辨率缩小倍数：默认为`No Scale`。提高缩小倍数可以使预览视频更流畅，但视频质量会更差。

   - 显示触摸位置：默认为false。打开后可以实时显示预览输入的触摸位置。
3. 音频选项

   - 音频源类型：默认为`APIOnly`。**注意：`AudioSourceName`/`AudioListenerName`输入的是AudioSource/AudioListener所挂载的GameObject的名称。**

     - `APIOnly`：只传输由API触发的音频。

     - `AudioSource`：由`AudioSourceName`指定一个AudioSource，只传输该AudioSource生成的音频。

     - `AudioListener`：由`AudioListenerName`指定一个AudioListener，只传输该AudioListener接收的音频。

   - 音频码率：默认为0～1000kbits/sec。最小/最大值范围为0～1000kbits/sec。
4. 网络选项
   - IP：会自动列出本机IP地址列表，需要选择与预览设备处于相同网络的IP地址。**更改本机网络环境后Windows平台下需要手动刷新IP列表。**

## 注意事项

1. **插件提供对`Input System`输入的完全支持与对`InputManager`输入的部分支持。**
   1. **使用`Input System`输入时，确保`Event System`上挂载了`InputSystemUIInputModule`**
   2. **使用`InputManager`输入时，需使用`WeChat Preview/Runtime/PreviewInputModule`替换掉`Standalone Input Module`**

2. **插件提供对部分WXSDK的支持，详见下文已支持API。**

3. **插件提供对排行榜的部分支持，仅对新版排行榜（ScreenCanvas模式）提供支持。新版排行榜的使用方式详见[文档](https://wechat-miniprogram.github.io/minigame-unity-webgl-transform/Design/OpenData.html)与[排行榜Demo](https://github.com/wechat-miniprogram/minigame-unity-webgl-transform/tree/main/Demo/Ranking)**。

4. **音频源类型选择`AudioSource`/`AudioListener`时，`AudioSourceName`/`AudioListenerName`输入的是AudioSource/AudioListener所挂载的GameObject的名称。**

5. **Windows平台下，网络环境变化时需要手动刷新IP列表。**

6. **`Render Streaming`运行环境未修复时，点击开始运行会进行环境修复，需要等待编译完成后再次点击开始运行。**

7. **MacOS M系列芯片暂不支持预览安卓设备。**

## 已支持API

|                     API                     |          备注          |
| :-----------------------------------------: | :--------------------: |
|           SetMessageToFriendQuery           |   预览环境下始终返回true  |
|           GetAppAuthorizeSetting            |                        |
|                GetWindowInfo                |                        |
|              GetSystemSetting               |                        |
|              GetSystemInfoSync              |                        |
|       GetMenuButtonBoundingClientRect       |                        |
|            GetLaunchOptionsSync             |                        |
|             GetEnterOptionsSync             |                        |
|                GetDeviceInfo                |                        |
|               GetAppBaseInfo                |                        |
|                                             |                        |
|                   AddCard                   |                        |
|             AuthPrivateMessage              |                        |
|                  Authorize                  |                        |
|         CheckIsAddedToMyMiniProgram         |                        |
|                CheckSession                 |                        |
|                 ChooseImage                 |                        |
|                 ChooseMedia                 |                        |
|              ChooseMessageFile              |                        |
|             CloseBLEConnection              |                        |
|            CloseBluetoothAdapter            |                        |
|                CompressImage                |                        |
|             CreateBLEConnection             |                        |
|          CreateBLEPeripheralServer          |                        |
|               ExitMiniProgram               |                        |
|                ExitVoIPChat                 |                        |
|                 FaceDetect                  |                        |
|          GetAvailableAudioSources           |                        |
|         GetBLEDeviceCharacteristics         |                        |
|              GetBLEDeviceRSSI               |                        |
|            GetBLEDeviceServices             |                        |
|                  GetBLEMTU                  |                        |
|           GetBackgroundFetchData            |                        |
|           GetBackgroundFetchToken           |                        |
|               GetBatteryInfo                |                        |
|                 GetBeacons                  |                        |
|          GetBluetoothAdapterState           |                        |
|             GetBluetoothDevices             |                        |
|             GetChannelsLiveInfo             |                        |
|          GetChannelsLiveNoticeInfo          |                        |
|              GetClipboardData               |                        |
|        GetConnectedBluetoothDevices         |                        |
|           GetDeviceBenchmarkInfo            |                        |
|                GetExtConfig                 |                        |
|              GetFuzzyLocation               |                        |
|               GetGameClubData               |                        |
|              GetGroupEnterInfo              |                        |
|             GetInferenceEnvInfo             |                        |
|              GetLocalIPAddress              |                        |
|               GetNetworkType                |                        |
|               GetPhoneNumber                |                        |
|              GetPrivacySetting              |                        |
|             GetScreenBrightness             |                        |
|           GetScreenRecordingState           |                        |
|                 GetSetting                  |                        |
|                GetShareInfo                 |                        |
|               GetStorageInfo                |                        |
|                GetSystemInfo                |                        |
|             GetSystemInfoAsync              |                        |
|                 GetUserInfo                 |                        |
|          GetUserInteractiveStorage          |                        |
|                GetWeRunData                 |                        |
|                HideKeyboard                 |                        |
|                 HideLoading                 |                        |
|                HideShareMenu                |                        |
|                  HideToast                  |                        |
|               InitFaceDetect                |                        |
|           IsBluetoothDevicePaired           |                        |
|                JoinVoIPChat                 |                        |
|                    Login                    |                        |
|              MakeBluetoothPair              |                        |
|           NavigateBackMiniProgram           |                        |
|            NavigateToMiniProgram            |                        |
|     NotifyBLECharacteristicValueChange      |                        |
|           OpenAppAuthorizeSetting           |                        |
|            OpenBluetoothAdapter             |                        |
|                  OpenCard                   |                        |
|            OpenChannelsActivity             |                        |
|              OpenChannelsEvent              |                        |
|              OpenChannelsLive               |                        |
|           OpenChannelsUserProfile           |                        |
|           OpenCustomerServiceChat           |                        |
|       OpenCustomerServiceConversation       |                        |
|             OpenPrivacyContract             |                        |
|                 OpenSetting                 |                        |
|         OpenSystemBluetoothSetting          |                        |
|                PreviewImage                 |                        |
|                PreviewMedia                 |                        |
|         ReadBLECharacteristicValue          |                        |
|                RemoveStorage                |                        |
|           RemoveUserCloudStorage            |                        |
|                 ReportScene                 |                        |
|          RequestMidasFriendPayment          |                        |
|             RequestMidasPayment             |                        |
|         RequestMidasPaymentGameItem         |                        |
|           RequestSubscribeMessage           |                        |
|        RequestSubscribeSystemMessage        |                        |
|           RequirePrivacyAuthorize           |                        |
|             RestartMiniProgram              |                        |
|               SaveFileToDisk                |                        |
|           SaveImageToPhotosAlbum            |                        |
|                  ScanCode                   |                        |
|                  SetBLEMTU                  |                        |
|           SetBackgroundFetchToken           |                        |
|              SetClipboardData               |                        |
|            SetDeviceOrientation             |                        |
|               SetEnableDebug                |                        |
|             SetInnerAudioOption             |                        |
|               SetKeepScreenOn               |                        |
|                SetMenuStyle                 |                        |
|             SetScreenBrightness             |                        |
|              SetStatusBarStyle              |                        |
|             SetUserCloudStorage             |                        |
|          SetVisualEffectOnCapture           |                        |
|               ShowActionSheet               |                        |
|                ShowKeyboard                 |                        |
|                 ShowLoading                 |                        |
|                  ShowModal                  |                        |
|             ShowShareImageMenu              |                        |
|                ShowShareMenu                |                        |
|                  ShowToast                  |                        |
|             StartAccelerometer              |                        |
|            StartBeaconDiscovery             |                        |
|       StartBluetoothDevicesDiscovery        |                        |
|                StartCompass                 |                        |
|         StartDeviceMotionListening          |                        |
|              StopAccelerometer              |                        |
|             StopBeaconDiscovery             |                        |
|        StopBluetoothDevicesDiscovery        |                        |
|                 StopCompass                 |                        |
|          StopDeviceMotionListening          |                        |
|               StopFaceDetect                |                        |
|               UpdateKeyboard                |                        |
|               UpdateShareMenu               |                        |
|          UpdateVoIPChatMuteConfig           |                        |
|               UpdateWeChatApp               |                        |
|                 VibrateLong                 |                        |
|                VibrateShort                 |                        |
|         WriteBLECharacteristicValue         |                        |
|                StartGameLive                |                        |
|            CheckGameLiveEnabled             |                        |
|         GetUserCurrentGameliveInfo          |                        |
|          GetUserRecentGameLiveInfo          |                        |
|           GetUserGameLiveDetails            |                        |
|         OpenChannelsLiveCollection          |                        |
|                  OpenPage                   |                        |
|        RequestSubscribeLiveActivity         |                        |
|              OpenBusinessView               |                        |
|                                             |                        |
|               ExitPointerLock               |                        |
|          OperateGameRecorderVideo           |                        |
|              RemoveStorageSync              |                        |
|                 ReportEvent                 |                        |
|              ReportPerformance              |                        |
|      ReportUserBehaviorBranchAnalytics      |                        |
|             RequestPointerLock              |                        |
|             ReserveChannelsLive             |                        |
|               RevokeBufferURL               |                        |
|               SetStorageSync                |                        |
|               ShareAppMessage               |                        |
|                  TriggerGC                  |                        |
|                                             |                        |
|            OnAccelerometerChange            |                        |
|           OffAccelerometerChange            |                        |
|          OnAudioInterruptionBegin           |                        |
|          OffAudioInterruptionBegin          |                        |
|           OnAudioInterruptionEnd            |                        |
|           OffAudioInterruptionEnd           |                        |
|         OnBLEConnectionStateChange          |                        |
|         OffBLEConnectionStateChange         |                        |
|               OnBLEMTUChange                |                        |
|               OffBLEMTUChange               |                        |
|    OnBLEPeripheralConnectionStateChanged    |                        |
|   OffBLEPeripheralConnectionStateChanged    |                        |
|            OnBackgroundFetchData            |                        |
|            OnBeaconServiceChange            |                        |
|           OffBeaconServiceChange            |                        |
|               OnBeaconUpdate                |                        |
|               OffBeaconUpdate               |                        |
|        OnBluetoothAdapterStateChange        |                        |
|       OffBluetoothAdapterStateChange        |                        |
|           OnBluetoothDeviceFound            |                        |
|           OffBluetoothDeviceFound           |                        |
|               OnCompassChange               |                        |
|              OffCompassChange               |                        |
|            OnDeviceMotionChange             |                        |
|            OffDeviceMotionChange            |                        |
|          OnDeviceOrientationChange          |                        |
|         OffDeviceOrientationChange          |                        |
|                   OnError                   |                        |
|                  OffError                   |                        |
|                   OnHide                    |                        |
|                   OffHide                   |                        |
|        OnInteractiveStorageModified         |                        |
|        OffInteractiveStorageModified        |                        |
|                  OnKeyDown                  |                        |
|                 OffKeyDown                  |                        |
|                   OnKeyUp                   |                        |
|                  OffKeyUp                   |                        |
|             OnKeyboardComplete              |                        |
|             OffKeyboardComplete             |                        |
|              OnKeyboardConfirm              |                        |
|             OffKeyboardConfirm              |                        |
|           OnKeyboardHeightChange            |                        |
|           OffKeyboardHeightChange           |                        |
|               OnKeyboardInput               |                        |
|              OffKeyboardInput               |                        |
|               OnMemoryWarning               |                        |
|              OffMemoryWarning               |                        |
| OnMenuButtonBoundingClientRectWeightChange  |                        |
| OffMenuButtonBoundingClientRectWeightChange |                        |
|                  OnMessage                  |                        |
|                 OnMouseDown                 |                        |
|                OffMouseDown                 |                        |
|                 OnMouseMove                 |                        |
|                OffMouseMove                 |                        |
|                  OnMouseUp                  |                        |
|                 OffMouseUp                  |                        |
|            OnNetworkStatusChange            |                        |
|           OffNetworkStatusChange            |                        |
|             OnNetworkWeakChange             |                        |
|            OffNetworkWeakChange             |                        |
|        OnScreenRecordingStateChanged        |                        |
|       OffScreenRecordingStateChanged        |                        |
|           OnShareMessageToFriend            |                        |
|                   OnShow                    |                        |
|                   OffShow                   |                        |
|            OnUnhandledRejection             |                        |
|            OffUnhandledRejection            |                        |
|             OnUserCaptureScreen             |                        |
|            OffUserCaptureScreen             |                        |
|            OnVoIPChatInterrupted            |                        |
|           OffVoIPChatInterrupted            |                        |
|          OnVoIPChatMembersChanged           |                        |
|          OffVoIPChatMembersChanged          |                        |
|          OnVoIPChatSpeakersChanged          |                        |
|         OffVoIPChatSpeakersChanged          |                        |
|           OnVoIPChatStateChanged            |                        |
|           OffVoIPChatStateChanged           |                        |
|                   OnWheel                   |                        |
|                  OffWheel                   |                        |
|               OnWindowResize                |                        |
|               OffWindowResize               |                        |
