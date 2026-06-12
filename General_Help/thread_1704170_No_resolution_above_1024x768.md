---
title: "No resolution above 1024x768"
date: 2011-03-10
forum: General Help
---

### Post by jxgreat on 2011-03-10
Well i have HP D2832. A very old CRT Monitor from HP  which have resolutions supported upto 1300 one but i can't get the resolutions after 1024x768. I want to get 1152x864 and cannot work to get it show in Monitors Panel.

In monitors panel it shows: Monitor: Unknown.

Please anyone help me i am finding this solution since one week.

Thanks in advance

---

### Post by searchfgold6789 on 2011-03-10
Well, you will probably have to edit your /etc/X11/xorg.conf file.
At a line near the bottom, it lists the available resolutions for your monitor, just add the one you want and reboot.
If it doesn't work you may have to be stuck with the smaller resolution!
The file might be in one of the places on [this page]("http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html") instead.

---

### Post by jxgreat on 2011-03-10
No Xorg file found anywhere

anyone else?????????//

i am using Ubuntu 10.10

---

### Post by jxgreat on 2011-03-10
Sorry everyone for disturbing i just found out my solution by following whats there

[http://ubuntuforums.org/showthread.php?t=1437980](http://ubuntuforums.org/showthread.php?t=1437980)

---

