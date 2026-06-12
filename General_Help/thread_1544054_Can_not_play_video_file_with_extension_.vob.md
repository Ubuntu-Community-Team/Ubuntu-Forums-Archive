---
title: "Can not play video file with extension .vob"
date: 2010-08-02
forum: General Help
---

### Post by MiTavis on 2010-08-02
When trying to play video files with the extension .vob, I get the following message:
 
pa_stream_writable_size () failed. Connection terminated. I tried to follow the tread associated with that error message with little luck. Following that thread led to the following command:
 
sudo pulseaudio  --kill
 
When I executed that command I got the following:
 
E: core-util.c: Home diectory home/username not ours
E:main.c: failed tokill daemon: permission denied
 
I only have one password on the system
 
 
Any ideas

---

### Post by MiTavis on 2010-08-02
The last thiong I did before the latest problem was to enter
 
sudo chown -r myusername ~/*
 
Does this help any viewer with an idea?

---

### Post by dino99 on 2010-08-02
vlc can play this format

---

### Post by krishnandu.sarkar on 2010-08-02
Ya download and install VLC.

---

### Post by MasterGamerJK on 2010-08-02
like stated before vlc is the best, but you can also compile multiple .vob files into a dvd iso, much liked youd get if you extracted a store bought dvd

---

### Post by MiTavis on 2010-08-02
That did solve the problem of not being able to play the vob file. I would still like to know why I got the error message when I tried to stop the process.

---

### Post by krishnandu.sarkar on 2010-08-03
There was no codec for it. Now try playing .vob in other players and you won't get errors now.

---

