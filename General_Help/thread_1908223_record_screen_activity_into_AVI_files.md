---
title: "record screen activity into AVI files"
date: 2012-01-13
forum: General Help
---

### Post by cold37 on 2012-01-13
im looking for a good record screen for ubuntu 11.10 i have Desktop recorder, Istanbul Desktop Session Recorder, XVidCap Screen Capture all them just are not that good i want some easy to use that dont drive me nuts try to make it work is this one that works with wine i can get?

---

### Post by carl4926 on 2012-01-13
Try these. 
Depending on your system, the first might be easier on your system

 p, li { white-space: pre-wrap; }  ```
ffmpeg -f x11grab -s `xdpyinfo | grep 'dimensions:'|awk '{print $2}'` -r 25 -i :0.0 -sameq output.mkv
```
```
ffmpeg -f x11grab -s `xdpyinfo | grep 'dimensions:'|awk '{print $2}'` -r 30 -qscale 1 -i :0.0 output.mkv

```

Obviously you need ffmpeg installed
You can change the .mkv to .avi but .mkv is better, you can convert it later if you must

---

### Post by cold37 on 2012-01-13
i have all the gstreamer plugins and ubuntu-restricted-addons i just want a video record that not such a bitch to use

---

