---
title: "installed live cd, but want server environment"
date: 2010-06-04
forum: General Help
---

### Post by ZenMasta on 2010-06-04
I was having trouble with my install media or maybe my RW. Anyway, I couldn't install using the server iso so I installed from a desktop live cd: 10.04 64bit.

I'd like to upgrade my startup environment to be more like the server install. ie without x starting etc.

I've installed openssh-server and performed an automatic update, that's all. I don't care about removing various applications pre-installed like open office and whatever other misc apps. 

I just want to disable x and any other startup apps so I am only booting up with the same services running as I would get if I installed from the server iso.

Thanks.

---

### Post by oldos2er on 2010-06-04
In /etc/default/grub, change the line "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to "GRUB_CMDLINE_LINUX_DEFAULT="text" ". When you reboot, you should be console mode. You can then use aptitude or apt-get to remove X, ubuntu-desktop, or whichever GUI apps you don't need.

I like the program sysv-rc-conf for controlling services.

---

### Post by ZenMasta on 2010-06-04
I don't necessarily want uninstall gdm/x just want to prevent it from starting.

I searched the forum but it seems the newest topics I had concerning this were from like 2007 or older. There was one topic that mentioned changing inittab and some setting to 3 for initdefault but seems like in this version there is no inittab file.

One topic was saying that simply doing that is simpler than trying to remove gdm since gdm can't/wont run without it in the first.

---

### Post by oldos2er on 2010-06-05
There hasn't been an /etc/inittab for a long time; it's been replaced by Upstart.

---

