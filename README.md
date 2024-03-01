```python
# 影片分割成圖片
import cv2 as cv
import os
# 打開影片文件
video_path = '您的影片文件路徑.mp4'  # 替換為您的影片文件路徑

cap = cv.VideoCapture(video_path)

#如指定目錄不存在就建立該目錄
path = 'video'
if not os.path.isdir(path):
    os.mkdir(path)

# 確保影片文件成功打開
if not cap.isOpened():
    print("無法打開影片文件")
    exit()

frame_count = 0

while True:
    # 讀取一帧
    ret, frame = cap.read()
    # 如果影片結束，則退出循環
    if not ret:
        break
    # 保存當前幀為圖像到指定路徑
    output_file = f"video/frame_{frame_count}.jpg"  # 每個幀都保存為一個單獨的圖像文件
    cv.imwrite(output_file, frame)
    
    frame_count += 1

# 釋放影片文件
cap.release()

# 顯示共分割多少張
print(f"共分割了 {frame_count} 幀圖像")
```
