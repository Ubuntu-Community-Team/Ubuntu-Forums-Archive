---
title: "Dual OS systems Windows 7 and Ubuntu"
date: 2012-07-18
forum: General Help
---

### Post by KaisaUbun2 on 2012-07-18
I have a Dell XPS l702x with a hybrid Nvidia graphic card, Ubuntu hasn't quite figured out how to make that work yet so that all my Hdmi ports work even with bumblebee since it is still in development phase. Also my SD card port is unfunctional with ubuntu, however I'm a firm believer in Ubuntu and in many many many many aspects find it better than windows 7, here is my dilemma I have some essentials i have grown used to (i.e. Itunes, netflix, and video games) So here is my question: 

If I install windows 7 first with all drivers, then install Ubuntu (250gb each) , then run a virtual box in Ubuntu running the windows 8 Consumer preview, will the drivers needed, be installed in windows 8 so that hdmi ports etc. will work? or would I have to reinstall drivers in the virtual box of windows 8 and is that even possible?

---

### Post by SigmaSanti on 2012-07-18
SD Card problem (assuming its the same problem as the l502x)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/995743]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/995743")
[http://askubuntu.com/questions/95391/how-do-i-mount-an-sd-card](http://askubuntu.com/questions/95391/how-do-i-mount-an-sd-card)[http://askubuntu.com/questions/95391/how-do-i-mount-an-sd-card]("http://askubuntu.com/questions/95391/how-do-i-mount-an-sd-card")

Using virtual box to access hdmi will probably not work, it is my understanding the the vm wraps around the host OS' graphics drivers, so if ubuntu's nvidia driver is not showing the hdmi port, then the vm will probably not see it. 

What you can do is buy a mini-displayport to hdmi converter. This will let you use hdmi in ubuntu because the displayport is part of the intel card.

---

