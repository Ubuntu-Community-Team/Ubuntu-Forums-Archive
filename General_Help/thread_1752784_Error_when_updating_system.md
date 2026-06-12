---
title: "Error when updating system"
date: 2011-05-08
forum: General Help
---

### Post by sokekoke on 2011-05-08
From my syslog:
kernel: [  581.831716] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
kernel: [  581.831721] ata1.00: BMDMA stat 0x24
kernel: [  581.831726] ata1.00: failed command: READ DMA EXT
kernel: [  581.831733] ata1.00: cmd 25/00:08:3b:65:81/00:00:2d:00:00/e0 tag 0 dma 4096 in
kernel: [  581.831735]          res 51/40:00:3d:65:81/40:00:2d:00:00/00 Emask 0x9 (media error)
kernel: [  581.831739] ata1.00: status: { DRDY ERR }
kernel: [  581.831741] ata1.00: error: { UNC }

Happens every time i update... it just spam the above error over and over ;(

tried to make an options.conf as suggested in this thread:
[http://ubuntuforums.org/showthread.php?t=1117102](http://ubuntuforums.org/showthread.php?t=1117102)

Still get the error though.. :(

---

### Post by sokekoke on 2011-06-06
UGH.

I now get this error at random, sometimes when I run firefox, netbeans or other programs. 

Any suggestions? :-S

---

### Post by Matt__ on 2011-06-06
do you have SMART enabled in the bios?

the fix seems to backport to lucid kernel [as described here on launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/591532")

found in the archives:
[quote=hobong]March 26th, 2009, 11:38 PM
It's Kernel Bug on ata ACPI. I put "options libata noacpi=1" on /etc/modprobe.d/options and the ERROR is gone.[/quote]

and this
[quote=jaycakep]March 23rd, 2010, 12:11 PM
have you try to restart udev, it's work on my laptop
sudo /etc/init.d/udev stop
sudo /etc/init.d/udev start[/quote]
but this will need to be done everytime you reboot.

---

### Post by sokekoke on 2011-06-06
Thanks for the suggestions Matt.

I have already tried the fix with "options libata noacpi=1" and this didn't have any effect.

I will try to run the stop/start udev commands and report back how it works out.

Else I will probably try to back-port my kernel, thanks for the tip.

---

### Post by sokekoke on 2011-06-07
Amazing!
I have created a bash script that runs when i start my system:
```
sudo stop udev
sudo start udev
```
It seems to fix all the nasty errors for now...

---

