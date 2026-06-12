---
title: "boot options"
date: 2010-04-28
forum: General Help
---

### Post by wojciech06 on 2010-04-28
I have 3 operating systems on my computer: Xp, Windows 7, and recently installed Ubuntu. When I boot my PC I get a screen with with boot options: Ubuntu 9.10 kernel..., recovery mode etc. At the bottom there's a line saying Microsoft Windows.[IMG]http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot[/IMG]
All Ubuntu options are working fine, and when I select Microsoft Windows, another screen pops up where I have to choose between Windows 7 and Windows XP. This is exactly what I had before installing Ubuntu.

Is there any way of changing these boot options so I can have all 3 operating systems displayed on one screen, and then how could I edit  them? I want to change the names, and the default operating system.

---

### Post by klemes on 2010-04-28
Well it depends on your version of GRUB.It sounds as you have GRUB2.If you had GRUB-legacy the editing on the relative configuration files would be quite  straightforward but in GRUB2 (grub-pc) it requires fiddling with the files in /etc/grub.d directory (mainly 30_os-prober and also 40_custom)and also being relatively recent limits the number of people that can answer your question,including me I am afraid....if it was about me I would live with this  for the time being but if you insist to change this and no-one else comes into aid presenting the solution there is an excellent Ubuntu wiki page devoted to GRUB2:

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by towheedm on 2010-04-28
Have a look at the last post in this thread:

[http://ubuntuforums.org/showthread.php?t=1464112](http://ubuntuforums.org/showthread.php?t=1464112)

---

