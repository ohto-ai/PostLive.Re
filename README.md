# PostLive.Re

PostLive 客户端的一个重构 / 实验版本 —— 基于 Qt 5.15 与 FFmpeg 的桌面直播客户端，属于学习型项目。

![login](doc/img/login.png)

## 功能

- Qt Widgets 登录界面，带启动动画与账号密码输入
- 登录后进入主窗口
- 基于 FFmpeg 的视频输入与预览
  - 摄像头输入
  - GDI 屏幕 / 窗口捕获
  - 本地视频文件输入（支持拖放）
- 视频参数与设备配置对话框
- Windows 下通过 GDI 枚举窗口并作为采集源
- 日志与调试辅助

## 环境要求

| 组件 | 版本 |
|---|---|
| 操作系统 | Windows 10 / 11 x64 |
| IDE | Visual Studio 2022 |
| Qt | 5.15.2 `msvc2019_64`（Qt VS Tools） |
| C++ | C++17 |
| FFmpeg | 放在 `3rd/ffmpeg/`（include + lib） |

## 构建

1. 确认 `3rd/ffmpeg/include` 与 `3rd/ffmpeg/lib` 存在。
2. 用 Visual Studio 打开 [`PostLive.sln`](PostLive.sln)。
3. 在 Qt VS Tools 中选择 Qt `5.15.2_msvc2019_64`。
4. 选择 `Release | x64`（或 `Debug | x64`）构建并运行。

## 运行

程序启动后先显示登录窗口；登录成功后进入主窗口。主窗口可以：

- 选择摄像头或窗口作为视频源
- 预览视频
- 选择本地视频文件
- 打开配置对话框调整参数

## 项目结构

```text
PostLiveClient/
├── main.cpp                 程序入口、登录与启动动画
├── PostLiveClient.*         主窗口
├── LoginPanel.*             登录界面
├── CameraHelper.*           摄像头辅助
├── components/              通用 UI 组件（拖放区、配置对话框等）
├── ffmpeg/                  FFmpeg 输入设备、解码与预览控件
├── form/                    Qt Designer 界面文件
└── res/                     图标与资源
doc/img/login.png            截图
```

## 说明

- 本项目与 [`PostLive`](https://github.com/ohto-ai/PostLive) 共享历史，是客户端部分的重构版本。
- 项目为学习 / 课程性质，功能与接口可能不完整，请勿直接用于生产环境。
- 推流服务端配置（Nginx + nginx-rtmp-module）可参考 PostLive 仓库的 `doc/` 目录。

## License

[MIT](LICENSE.txt)
