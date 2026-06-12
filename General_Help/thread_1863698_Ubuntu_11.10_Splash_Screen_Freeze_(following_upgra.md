---
title: "Ubuntu 11.10 Splash Screen Freeze (following upgrade)"
date: 2011-10-18
forum: General Help
---

### Post by stoll on 2011-10-18
Hello,

I seem to have run into problems with my Ubuntu 11.04 to 11.10 upgrade. 

The upgrade appeared to be successful and I was able to restart and login once.

However all following restarts result in a freeze at the Ubuntu splash screen. 

I am able to login via Recovery mode in shell, however when checking syslog, messages or boot logs I am unable to locate anything out of the ordinary.

Has anybody else experienced this issue? Would anybody be able to suggest fixes or ways that could help identify the source of the problem?

Thanks in advance.

---

### Post by stoll on 2011-10-18
Ok seem to have solved this, believing it to be a graphical issue. For anybody else experiencing similar problems, I did the following:

Booted into recovery mode and logged in on command line.

Checked everything was up to date, reinstalled gdm and xorg:
$ sudo apt-get update && sudo apt-get upgrade
$ sudo apt-get install --reinstall gdm xorg

Removed xorg.conf so that a new one was created upon boot:
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.faulty
$ sudo reboot

Now rebooted into Ubuntu 11.10 and voila, everything is better!

Hope it helps

---

