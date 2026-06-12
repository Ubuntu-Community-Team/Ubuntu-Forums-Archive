---
title: "Another Webcam Issue...."
date: 2011-10-20
forum: General Help
---

### Post by berkboss on 2011-10-20
Hi, My friend has a Sony Vaio VGN-FE770G that I helped him breath new life into by convincing him Ubuntu is better than windows XP.

Everything is working great except for the webcam. I've tried downloading and running r5u87x but it still says no devices found... Any ideas?

Thanks,

Berk Bossard

---

### Post by no2498 on 2011-10-21
have him install guvcview
then in a terminal type dmesg click inter
after it stops type lsusb click enter
now try the cam in guvcview
if its a lap top click the fn+f4 keys if he has the fn key
that turns the cam on

---

### Post by berkboss on 2011-10-21
Thank you! This solved the problem.

---

### Post by berkboss on 2011-11-15
The fix worked great until two days ago. Now every piece of software is saying there's not a webcam installed. I tried redoing the steps listed above, but it didn't help the situation any.

---

### Post by no2498 on 2011-11-16
if he tried the cam in vlc it changes the file type to like mpeg
reset the file type to avi in guvcview
may need to restart the computer
also can try this program wxcam
can get it in/as a deb file look at all files
[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)
hope this helps too

---

