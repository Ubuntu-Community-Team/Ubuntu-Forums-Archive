---
title: "Live USB: webcam did work, now can't find /dev/video0 ?"
date: 2009-06-27
forum: General Help
---

### Post by jorx on 2009-06-27
Hi everybody!
I have an important question at the moment-- 
I had a webcam (Logitech Quickcam PTZ) working perfectly time on one boot and making video calls with it.
Now, a week later, I've tried on the exact same machine and webcam- and it doesn't show up.

Running 'lsusb' at the command line lists the camera perfectly fine, but Skype doesn't detect it, and Camorama and gqcam says "could not connect to video device (/dev/video0)"

I have an inkling that live USB might be part of the problem- sometimes I have problem remounting hard-drives after a reboot- so have learned to do it by command line.

So is there a way to umount and then remount the webcam to /dev/video0 ?  

Thanks,
Jordan

---

