---
title: "xbmc remote stopped working"
date: 2012-05-18
forum: General Help
---

### Post by qwertyjjj on 2012-05-18
Since the Eden update and also some 11.10 updates, the remote only partially works now. It works in mouse mode where I can hold down a direction button and select options on the screen but in remote mode the up down left right buttons do not work, nor the My Video and My Music buttons do not work.
I used this to install originally: [http://forum.xbmc.org/showthread.php?tid=82772](http://forum.xbmc.org/showthread.php?tid=82772)
[http://wiki.xbmc.org/index.php?title=IRF_Media_W-01RN](http://wiki.xbmc.org/index.php?title=IRF_Media_W-01RN)

Any ideas how I can get it working again?

I followe this to try and learn to codes for the remote:[http://www.omcentre.com.au/hardware/m350-media-centre/wireless-multimedia-infrared-ir-remote-controller-deal-extreme-34435/](http://www.omcentre.com.au/hardware/m350-media-centre/wireless-multimedia-infrared-ir-remote-controller-deal-extreme-34435/)
but I'm not sure how to program presses like My Video and My TV


```

j-media-centre@jmediacentre-A880G:~/hid_mapper_beta$ sudo nano /usr/local/bin/irfmedia.map
j-media-centre@jmediacentre-A880G:~/hid_mapper_beta$ sudo ./hid_mapper --learn --lookup-id  --manufacturer 0755 --product 2626 --map ''
Found HID device
Opened HID interface on /dev/hidraw0
Opened HID interface on /dev/hidraw1
00 00 51 00 00 00 00 00 
00 00 00 00 00 00 00 00 
02 00 00 00 00 00 
00 00 52 00 00 00 00 00 
00 00 00 00 00 00 00 00 
02 00 00 00 00 00 
00 00 50 00 00 00 00 00 
00 00 00 00 00 00 00 00 
02 00 00 00 00 00 
00 00 4f 00 00 00 00 00 
00 00 00 00 00 00 00 00 
02 00 00 00 00 00 

```

---

