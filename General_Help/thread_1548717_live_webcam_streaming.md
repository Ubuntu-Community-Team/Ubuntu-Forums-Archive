---
title: "live webcam streaming"
date: 2010-08-08
forum: General Help
---

### Post by hwttdz on 2010-08-08
I have a webcam that works great with cheese/skype, but I'd like to set up a webcam (mostly for figuring out how to do it).  And thus far I've tried camserv and webcam-server, both with no luck.  

export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so; webcam-server -l webcam-server.log -v -g 320x240 -p 8888 -d /dev/video0

gives a "libv4l2: error reading: No such device"

webcam-server -l webcam-server.log -v -g 320x240 -p 8888 -d /dev/video0

gives a "get_cam_image(): len != img->bufsize, just letting you know"

camserv 

gives "bind(): Address already in use"

does anyone have any advice or know of a working webcam streaming app?

---

### Post by stlsaint on 2010-08-19
Maybe here....
[http://hacktivision.com/index.php/2009/06/16/setting-up-an-ubuntu-webcam-server?blog=2](http://hacktivision.com/index.php/2009/06/16/setting-up-an-ubuntu-webcam-server?blog=2)

NOTE: Ive never set this up so ensure all your data is backed up and safe as with any project you would work on!!

---

