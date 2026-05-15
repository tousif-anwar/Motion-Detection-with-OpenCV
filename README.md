# Motion Detection with OpenCV

This project implements a motion detection system using **OpenCV** and **Python**. The program captures video from a webcam, processes the frames to detect motion, and logs the timestamps when motion is detected.

## Features
- Captures live video using OpenCV
- Detects motion using frame differencing and contour detection
- Saves timestamps of motion events to a CSV file
- Displays processed frames in real-time

## Technologies Used
- Python 3
- OpenCV
- Pandas
- NumPy (optional, but recommended for performance optimization)

## Installation

1. **Clone the Repository:**
   ```sh
   git clone https://github.com/yourusername/motion-detection-opencv.git
   cd motion-detection-opencv
   ```
2. **Install Dependencies:**
   ```sh
   pip install -r requirements.txt
   ```

## Usage

Run the script to start motion detection:
```sh
python motion_detector.py
```

### Tunable Parameters

You can adjust these constants at the top of `motion_detector.py` for different environments:
- `BLUR_KERNEL_SIZE`: Size of Gaussian blur kernel (default: (11, 11))
- `THRESHOLD_VALUE`: Sensitivity threshold for motion detection (default: 30)
- `MIN_CONTOUR_AREA`: Minimum pixel area to consider as motion (default: 10000)
- `FRAME_WIDTH` / `FRAME_HEIGHT`: Video capture resolution (default: 640x480)

### Controls
- **Press 'q'** to quit the program.

## How It Works
1. The program initializes the webcam and captures the first frame.
2. Each new frame is converted to grayscale and blurred to reduce noise.
3. The difference between the first frame and the current frame is computed.
4. A threshold is applied to highlight moving objects.
5. Contours are detected, and if an object is large enough, it is considered motion.
6. Timestamps of motion events are recorded and saved in `Times.csv`.

## Output
The program generates a CSV file (`Times.csv`) with the timestamps of detected motion:

| Start Time | End Time |
|------------|---------|
| 2025-02-07 10:15:30 | 2025-02-07 10:15:45 |
| 2025-02-07 10:20:12 | 2025-02-07 10:20:25 |

## Potential Improvements
- Implement email or SMS notifications when motion is detected
- Save recorded video clips of motion events
- Improve accuracy with background subtraction methods

## Performance Optimizations

This project has been optimized for better performance:

1. **Reduced Blur Kernel Size**: Changed from (21, 21) to (11, 11) for ~4x faster Gaussian blur
2. **Frame Size Control**: Captures constrained to 640x480 for consistent, faster processing
3. **Eliminated Unnecessary Copy**: Removed `thresh_frame.copy()` as OpenCV 4+ doesn't modify findContours input
4. **Reduced Window Displays**: Shows only 2 windows (Threshold + Detection) instead of 4
5. **Optimized Status List**: Uses direct assignment instead of append + slice operations
6. **Configurable Constants**: All tunable parameters defined as constants for easy adjustment

These optimizations significantly reduce CPU usage while maintaining detection accuracy.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

Feel free to contribute and improve this project!

