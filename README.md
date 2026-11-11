# Qbox 可选播放组件

Qbox 基础安装包只带系统解码。本仓库托管可选的播放组件 ZIP，由 Qbox 应用在“设置 → 播放器”中按需下载，不随 APK 分发。

## 组件

| 组件 | ABI | 文件 | ZIP 字节数 | 展开字节数 | SHA-256 |
| --- | --- | --- | ---: | ---: | --- |
| MPV/FFmpeg（增强解码） | ARM64 | `qbox-enhanced-1-arm64-v8a.zip` | 19,891,521 | 44,864,256 | `99b55aeea3c3c651ade7e123a38a1278e21b1463ed4f4fc9bc1c6c87e26e2cf2` |
| MPV/FFmpeg（增强解码） | ARM32 | `qbox-enhanced-1-armeabi-v7a.zip` | 18,463,671 | 38,718,248 | `ff194f73b20e7032e9499c0b0de96fc1b96212a0e010d9b2b79587bc012dc2f1` |
| X5 内核 046239 | ARM64 | `qbox-x5-1-arm64-v8a.zip` | 48,309,648 | 48,646,114 | `d2db4c228b25cbdb090d7693d7b01cfe02585b9ccefbcc4abfe4c36c3588fc0d` |
| X5 内核 046250 | ARM32 | `qbox-x5-1-armeabi-v7a.zip` | 42,115,916 | 42,579,915 | `0690e244fe67ee99c34bef4b2f2a1cdc1d00b944b0f8930164b6fe7346bdc1fd` |

组件包内固定清单、包级与逐文件长度/SHA-256 与 Qbox 0.3.39-dev 的 `app/src/main/assets/qbox/components.json` 一致。应用下载后会先校验整包 SHA-256，再校验解压后的每个文件，校验不通过不会安装。

## 下载地址

Qbox 构建时把组件根地址固定为：

```text
https://raw.githubusercontent.com/qjy0128/qbox-components/v1/
```

对应文件即上表文件名。`v1` 是标签，内容不再变化；更换组件版本会发布新的标签并在应用中更新清单。

## 适用版本

- 应用版本 `0.3.39-dev`（versionCode 46），`components.json` 允许 `minAppVersionCode=45`～`maxAppVersionCode=46`。
- ARM64 与 ARM32 组件按设备 ABI 选择，应用只下载匹配当前 ABI 的包。

## 使用说明

1. 安装 Qbox 基础包（手机或电视，ARM64/ARM32 对应）。
2. 打开“设置 → 播放器”，点击“增强解码”或“X5 内核”下载。
3. 下载完成后按提示重启应用或启用 X5。

## 来源与边界

- MPV/FFmpeg 组件为 Qbox 自建原生库打包。
- X5 内核为腾讯浏览服务（TBS）离线内核二进制，仅作家庭自用分发，版权归腾讯所有；如需商用请自行取得授权。
- 本轮 ARM32 组件未做设备运行验收；ARM64 组件在小米电视 `MiTV-MFFU0`（Android 14）上完成过下载、加载与播放验证，详见 Qbox 仓库的验收记录。
