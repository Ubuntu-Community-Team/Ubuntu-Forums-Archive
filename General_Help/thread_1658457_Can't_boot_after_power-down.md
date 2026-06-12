---
title: "Can't boot after power-down"
date: 2011-01-02
forum: General Help
---

### Post by shonlittle on 2011-01-02
I have searched and searched and can't find any information on this.

Whenever I power-down my CPU (not reboot, full power-down) my Ubuntu system will not boot up.  No other OS is on the computer, just Ubuntu.  Usually reinstalling grub will fix the boot problem.  But I don't understand why simply turning off the computer would mess up grub.  I have to keep my computer running 24/7 or I have to go through the process of rescuing the system.

I'm guessing it's something to do with the hardware and not the OS.

Any ideas?

---

### Post by DasEi on 2011-01-02
A little vague info you gave here, what does that mean "does not boot" ?
seems it boots and then either throws an error or hangs with black
screen or busybox.
As of now you seem running, :
sudo apt-get install hwinfo pastebinit && sudo hwinfo |pastebinit
-give resulting url here -
pastebinit /var/log/syslog
-give...

DasEi

---

### Post by Hippytaff on 2011-01-02
if you can post the results of the boot script here [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
it might shed some light on the issue.

---

