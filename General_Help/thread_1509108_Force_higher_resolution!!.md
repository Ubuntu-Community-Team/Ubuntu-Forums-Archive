---
title: "Force higher resolution!!"
date: 2010-06-13
forum: General Help
---

### Post by Browner87 on 2010-06-13
I have an old computer that I use as a web/file/print server and I just put 10.04 on it, but my problem is that I don't have a monitor hooked to it. I always just use VNC to remote access it. However, since no monitor is detected, it refuses to let me use a reasonable resolution (1280x768 for example). 

I've looked here :[http://superuser.com/questions/139073/how-to-add-higher-video-resolution-in-ubuntu-10-04-unr-on-eee1101ha](http://superuser.com/questions/139073/how-to-add-higher-video-resolution-in-ubuntu-10-04-unr-on-eee1101ha)

and had no luck. It gave me the error "
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  18
  Current serial number in output stream:  18"

My exact line was: "xrandr --newmode "1280x768_60.00" 79.50 1280 1344 1472 1664 768 771 781 798 -hsync +vsync"

Can anyone help? It's much easier to manage a server with a resolution above 960x600.

---

