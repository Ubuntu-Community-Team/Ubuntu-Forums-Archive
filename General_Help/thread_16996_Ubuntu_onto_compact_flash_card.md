---
title: "Ubuntu onto compact flash card"
date: 2005-02-25
forum: General Help
---

### Post by whurley on 2005-02-25
I have installed ubuntu 4.10 (kernel 2.6.8.1-3) onto a 512MB Compact Flash card

I used the HOWTO from [http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)  to install a minimal system.

I am using xdm and iceWM

I want to know 2 things

1: How can I stop any disk writing. I dont want a fully read only system, I may want to make changes or upgrades in the future, but I want to stop any system logs, swap activity etc.

2: How to autlogin. It currently shows a boring grey login screen. I dont want to change my display or window manager, because of the limited space available.

My linux knowledge is very limited. To get this far has been hard enough!

---

### Post by whurley on 2005-02-25
I figured out the autologin. 

I have switched to gdm instead of xdm (after freeing up a bit of space).

In /etc/X11/gdm/gdm.conf

AutomaticLoginEnable=true
AutomaticLogin=username

 :p

---

### Post by whurley on 2005-02-25
I have got removed klogd and sysklogd

Also edited fstab
'noatime' option for /
comment out swp

---

