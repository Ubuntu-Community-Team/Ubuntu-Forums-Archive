---
title: "Wiimote on PS3"
date: 2009-11-19
forum: General Help
---

### Post by Jiffyman on 2009-11-19
I just got a new PS3 and decided to install linux on it. I went with Ubuntu 9.04 for PS3. While playing around I thought that it would be cool to get the Wiimote working with it like I had seen in a video. Unfortunately it doesn't seem to be well documented on the ps3, but I found a guide for ubuntu and tried it. I download lswm, wmgui and wminput.  I added uinput to /etc/modules and even tried to start it manually using.
 
```
modprobe uinput
``` When I tried to start wminput I get this error 

```
wminput -c ir_ptr
``````
error on uinput ioctl
```

I looked it up and found this page:

[http://ubuntuforums.org/showthread.php?t=535659&page=13](http://ubuntuforums.org/showthread.php?t=535659&page=13)

which led me to this page:

[http://www.keshi.org/moin/PS3/WiiRemote](http://www.keshi.org/moin/PS3/WiiRemote)

**So I guess my main question is how do I patch the files talked about in the second link? Do they want me to patch the sources or the programs themselves? The person who wrote the article gave vague instructions.**

---

### Post by Jiffyman on 2009-11-19
Can anyone tell me how to patch the appropriate files. I can start the patcher I just don't know what files to point it to. I have confirmed that I can connect the wiimote to my PS3 with wmgui.

---

### Post by Jiffyman on 2009-11-20
PLEASE..... Does anyone have anything, anything at all.

---

