---
title: "Monitor lost signal"
date: 2012-07-02
forum: General Help
---

### Post by Tema1 on 2012-07-02
This morning I turned on the computer, all started normally, then right before the welcome screen my monitor lost the signal. I restarted 3 times and all are the same. Turned off power to computer and monitor, restarted and still lost signal. I used the CD (12.04) to log in and I finally managed to get a display and managed to into my system. I have no idea how to proceed from here. I certainly would like to get back to logging in from my HD and not the CD. I know you need more info, but I have no idea how to get it.
 
Please help if you can.
 
Thanks,
Tema1

---

### Post by dino99 on 2012-07-02
if you can boot with an other kernel, then do; otherwise try the recovery mode.

 There, delete xorg.conf if it exist (sudo rm /etc/X11/xorg.conf)
watch the logs for errors (.xsession-errors & /var/log/)
check that graphic driver is activated (sudo jockey-gtk) (if you are using gnome indeed)

---

### Post by Tema1 on 2012-07-03
I used Boot Repair while I was using the live CD and everything is good now.
 
[http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/](http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/)
 
Thanks for the help ):P
 
Tema1

---

