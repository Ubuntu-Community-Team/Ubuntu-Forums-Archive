---
title: "Trouble with partitions"
date: 2011-03-25
forum: General Help
---

### Post by Dampmeat on 2011-03-25
I have ubuntu 10.04 right now and I have a digital copy of windows 7. When I run the windows 7 setup with wine it will begin to install but then will say i don't have enough space on my partitions. So I went and tried to make room but I really wasn't sure what I was doing, how do I set aside free space in my partitions for windows to install itself into?

---

### Post by slooksterpsv on 2011-03-25
You won't be able to install Windows via WINE.

When you installed Ubuntu did you leave at least 40+GB of Space for Windows 7? 
If not you'll need to boot off of a Live CD, install gparted (if its not under System -> Administration), and "shrink" your Ubuntu installation by at least 40GB if you have the space, I say 40GB, cause the install of Win 7 takes 20GB, and updates take about another 10-15GB.

How large of a Hard Drive is in your machine? Do you know if you allocated all space to Ubuntu or if you left it some space?

Another option, if you just need Windows 7 for a few programs and not to run mainly, is to use VirtualBox and install Windows 7 in VirtualBox, then you can boot to it while in Linux (although performance may suffer a bit, and games won't work).

---

