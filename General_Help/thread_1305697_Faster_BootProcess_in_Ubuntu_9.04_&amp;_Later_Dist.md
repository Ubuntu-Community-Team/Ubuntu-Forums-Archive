---
title: "Faster BootProcess in Ubuntu 9.04 &amp; Later Dist"
date: 2009-10-30
forum: General Help
---

### Post by aditya.gnu on 2009-10-30
Hello Ubuntu Geeks,
I am a huge fan of Ubuntu and I am passinate about Linux OS.
Well, coming to the point, I wanted to understand **how's the booting time of Ubuntu 9.04(exclusively) made so fast as compared to previous Versions of Ubuntu**.
Whats the important module/function/which file is behind, that makes the OS boot time so less or how does it work at the background?I want to know the complete details of that. 
 
And **is it possible to make any Debian based Distro boot in the same manner**? 
 
If any one you of has done it/explored it before, or if you know it , kindly send me the detials.(Links/URL's are also entertained).
 
Thanks and Regards,
Aditya.

---

### Post by theozzlives on 2009-10-30
Ubuntu IS a Debian based distro, and I believe it's the ext4 filesystem.

---

### Post by P4man on 2009-10-30
Nah, its not Ext4. Ext4 helps but only marginally. The secret sauce is upstart, and apparently that is an option in debian as well:
[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

