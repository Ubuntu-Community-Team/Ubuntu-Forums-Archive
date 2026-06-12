---
title: "VNC Setup"
date: 2012-08-04
forum: General Help
---

### Post by caligula2 on 2012-08-04
I catually turned my computer into a file server running 12.04 LTS 32-bit, but I also likee to do other stuff on it. I'm fairly new to ubuntu so I'm not to good with the command line, thus ssh is difficult for me. I want to connect to my computer using VNC. but I can'tfigure out how to get Ubuntu to start-up without the monitor. Any suggestions?

I already tried this method:
[http://olitee.com/2010/01/ubuntu-remote-desktop-without-a-monitor/](http://olitee.com/2010/01/ubuntu-remote-desktop-without-a-monitor/)

---

### Post by Geffers on 2012-08-04
> **caligula2 said:**
> I catually turned my computer into a file server running 12.04 LTS 32-bit, but I also likee to do other stuff on it. I'm fairly new to ubuntu so I'm not to good with the command line, thus ssh is difficult for me. I want to connect to my computer using VNC. but I can'tfigure out how to get Ubuntu to start-up without the monitor. Any suggestions?

I already tried this method:
[http://olitee.com/2010/01/ubuntu-remote-desktop-without-a-monitor/](http://olitee.com/2010/01/ubuntu-remote-desktop-without-a-monitor/)

Obviously initially with a monitor start up normally, then on 12.04 go to Applications, System Tools, System Settings. Scroll down to System, User Accounts then choose the Automatic Login option.

Geffers

---

### Post by caligula2 on 2012-08-04
That's not the problem. My computer will automatically log in. When I follow the instruction from that website I listed, all I get is that tty1 (or whatever it is) terminal asking me to log in. It seems like the graphics, or background, or whatever it is can't load.

---

### Post by caligula2 on 2012-08-06
On step 2 of this [site]("http://troylee2008.blogspot.com/2012/05/configure-ubuntu1204-to-boot-without.html?showComment=1344285922497#c824303349854051940"), when i try "echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf" or "sudo echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf" it says permission denied. any suggestions?

---

### Post by caligula2 on 2012-08-06
Day three of journey (or two; I can't remember). I fear that moral is beginning to dwindle. Each passing day seems to offer hope of a solution that I simply overlooked before, but the fates then use that hope to beat me down, as the true answer still eludes me. I have discovered that i needed to type "su," and in root I could type in the command. Alas, this was just another failed attempt. The humming of my computer reminds me of the ocean; I fear my sanity is slipping. In a different [article]("http://ubuntuforums.org/showthread.php?t=1452600&page=3"), I noticed that it said "**-nv** or -vesa" (my graphics card is nvidea). I don't really know what those mean, but I have become desperate, so I succumbed to the madness and replaced the vesa in my xorg.conf with nv. Light at the end of the tunnel! Once I restarted my computer, my monitor opened itself to me to reveal the desktop, as apposed to the tty1 terminal thing. However, once the computer had been restarted with the monitor unplugged, the vnc connection remained closed. I will continue chronicling my journey for anyone willing the read it, but I don't know how much longer I can last. I wonder if I'll die before this is resolved. I wonder... if I'll dream.

P.S. ssh still works fine.

---

### Post by Toz on 2012-08-09
Moved to new thread for the specific VNC question.

---

