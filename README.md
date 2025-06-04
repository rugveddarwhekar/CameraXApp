# CameraX App

A modern Android application that demonstrates the power and simplicity of CameraX API for camera operations. This app showcases how to implement a full-featured camera application with photo capture, video recording, and image analysis capabilities.

## 🚀 Features

- 📸 **Photo Capture**: Take high-quality photos and save them to device storage
- 🎥 **Video Recording**: Record videos with audio support
- 🔍 **Image Analysis**: Real-time image analysis with luminosity calculation
- 📱 **Modern UI**: Clean and intuitive user interface with Material Design 3
- 🔒 **Permission Handling**: Robust permission management for camera and storage access
- 📦 **MediaStore Integration**: Seamless integration with Android's MediaStore for media management

## 🏗️ Architecture

The app follows a clean architecture pattern with the following components:

```mermaid
graph TD
    A[MainActivity] --> B[CameraX Components]
    B --> C[Preview]
    B --> D[ImageCapture]
    B --> E[VideoCapture]
    B --> F[ImageAnalysis]
    C --> G[CameraProvider]
    D --> G
    E --> G
    F --> G
    G --> H[Camera Hardware]
```

### Component Flow

```mermaid
sequenceDiagram
    participant User
    participant MainActivity
    participant CameraX
    participant MediaStore
    
    User->>MainActivity: Launch App
    MainActivity->>MainActivity: Check Permissions
    MainActivity->>CameraX: Initialize Camera
    CameraX->>MainActivity: Camera Ready
    
    alt Take Photo
        User->>MainActivity: Click Photo Button
        MainActivity->>CameraX: Capture Image
        CameraX->>MediaStore: Save Photo
        MediaStore->>MainActivity: Photo Saved
    else Record Video
        User->>MainActivity: Click Video Button
        MainActivity->>CameraX: Start Recording
        User->>MainActivity: Click Stop Button
        MainActivity->>CameraX: Stop Recording
        CameraX->>MediaStore: Save Video
        MediaStore->>MainActivity: Video Saved
    end
```

## 🛠️ Technical Implementation

### Key Components

1. **CameraX Integration**
   - Uses CameraX 1.2.2 for modern camera operations
   - Implements Preview, ImageCapture, VideoCapture, and ImageAnalysis use cases
   - Handles camera lifecycle management

2. **Permission Management**
   - Runtime permission handling for camera and storage access
   - Graceful fallback for permission denials
   - Support for Android 10+ scoped storage

3. **Media Storage**
   - Integration with MediaStore API
   - Organized storage structure for photos and videos
   - Proper file naming and metadata management

### Dependencies

```gradle
dependencies {
    val cameraXversion = "1.2.2"
    implementation("androidx.camera:camera-core:${cameraXversion}")
    implementation("androidx.camera:camera-camera2:${cameraXversion}")
    implementation("androidx.camera:camera-lifecycle:${cameraXversion}")
    implementation("androidx.camera:camera-video:${cameraXversion}")
    implementation("androidx.camera:camera-view:${cameraXversion}")
    implementation("androidx.camera:camera-extensions:${cameraXversion}")
}
```

## 📱 UI/UX Design

The app features a clean and intuitive interface with:

- Full-screen camera preview
- Large, easily accessible capture buttons
- Clear visual feedback for recording state
- Material Design 3 theming support
- Dark mode compatibility

## 🔄 State Management

```mermaid
stateDiagram-v2
    [*] --> Initializing
    Initializing --> Ready: Permissions Granted
    Initializing --> PermissionDenied: Permissions Denied
    Ready --> TakingPhoto: Photo Button Pressed
    Ready --> RecordingVideo: Video Button Pressed
    TakingPhoto --> Ready: Photo Captured
    RecordingVideo --> Ready: Video Stopped
    PermissionDenied --> [*]: App Closed
```

## 🎯 Future Improvements

1. **Enhanced Features**
   - Add filters and effects
   - Implement HDR mode
   - Add slow-motion video support
   - Implement portrait mode

2. **UI Enhancements**
   - Add camera controls (flash, timer, etc.)
   - Implement gallery view
   - Add photo/video editing capabilities

3. **Performance Optimizations**
   - Implement image compression
   - Add background processing
   - Optimize memory usage

## 📝 Learning Resources

- [CameraX Documentation](https://developer.android.com/training/camerax)
- [Android MediaStore Guide](https://developer.android.com/training/data-storage/shared/media)
- [Material Design 3](https://m3.material.io/)

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License.
