ffmpeg

ffmpeg解码播放

FFmpeg -list_devices true -f video4linux2 -i dummy                                                        


ffmpeg -f dshow -i video="Integrated Camera" -vcodec libx264 ./001.mkv  

rtmp湖南卫视源
rtmp://58.200.131.2:1935/livetv/hunantv


一、摄像头信息采集和录制推流:
查询摄像头设备：ffmpeg -list_devices true -f dshow -i dummy

ffmpeg -f dshow -i video="Integrated Camera" -vcodec libx264 -acodec copy -preset:v ultrafast -tune:v zerolatency -f flv rtmp://192.168.1.111:1935/live 

二：录制屏幕
ffmpeg -f gdigrab -i desktop a.mp4

ffmpeg -f gdigrab -i desktop -vcodec libx264 -preset:v ultrafast -tune:v zerolatency -f flv rtmp://192.168.1.111:1935/live 

三：视频文件推流：

ffmpeg -re -i eguid.flv -vcodec copy -acodec copy -f flv -y

四：拉流
ffmpeg -i rtmp://192.168.1.111:1935/live -vcodec h264 -f flv -acodec aac -ac 2 a.flv
