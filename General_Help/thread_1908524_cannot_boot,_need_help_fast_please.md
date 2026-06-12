---
title: "cannot boot, need help fast please"
date: 2012-01-13
forum: General Help
---

### Post by liquidmonkey on 2012-01-13
so one day before we leave on vacation and i reboot my computer after doing an update and a clonezilla backup and guess what? i can't boot.

the ubuntu screen comes up, the little dots turn color and then a black screen with the messages at the bottom of this post.

i have tried to restore the backup image (i checked it twice to be sure it was ok and it is ok) but am still getting the same error.

have done a search in google for some of the terms below but no luck.
my laptop is a samsung series 9.

i really really really need some help here, thank you.

-------------------------------------------------------
starting mDNS/DNS-SD daemon
starting KVM
starting system V runlevel compatibility
starting CPU interrupts balancing daemon
starting network connection manager
stopping cold plug devices

*stopping log initial device creation
*starting enable remaining boot-time encrypted block devices
*starting configure network device security
*stopping enable remaining boot-time encrypted block devices
ueyeusb is running
*starting bluetooth
not starting as we're not running in a vm
*(red color) pulseaudio configured for per-user sessions
saned disable; edit /etc/default/saned
*checking battery state
---------------------------------------------

again, any help is very much appreciated!

---

### Post by Ryan.Laughlin on 2012-01-13
This may help you:
[http://http://ubuntuforums.org/showthread.php?t=1859820]("http://http//ubuntuforums.org/showthread.php?t=1859820")

Experiencing the same issue. I recently upgraded to 11.10.  Able to pull up terminal.  

I have a Radeon HD 3650 graphics card, so I installed the fglrx driver with 


Then I tried Installing Catalyst Manually (from AMD/ATI's site) as directed here: [http://wiki.cchtml.com/index.php/Ubu...talyst.2Ffglrx]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx"), 

Everything seems to go well.  start with removing the drivers, successfully, and make it all the way down to generic config.  

Restart and still stuck at Checking Battery [OK].  Go to terminal, and attempt fglrxinfo and again get:

Error: unable to open display(null)

I thought I was sure that the Radeon HD 3650 was supported by the fglrx driver, but maybe its not?
This is ruining my life.  PLEASE HELP

---

### Post by liquidmonkey on 2012-01-13
thanks for the tips but not too helpful for me.
i'm using a samsung series 9 laptop (90X3A) and the graphics are integrated.

i'm now able to get into the terminal so is there anything i can do from here?
maybe roll back to an earlier version, ie, before i did the latest update?
do a check disk of sorts?

really no idea but any suggestions are welcome :)

---

### Post by AEllerbrock on 2012-01-13
download Boot-Repair and burn it in a CD
the boot from that CD. Booting troubles are related to grub. this software fixes it.
Luck!

---

### Post by liquidmonkey on 2012-01-13
> **AEllerbrock said:**
> download Boot-Repair and burn it in a CD
the boot from that CD. Booting troubles are related to grub. this software fixes it.
Luck!

will give that go BUT this laptop has no cd :(
i'll c if i can use a usb instead.

thanks!


***leaves to try it out***

---

### Post by liquidmonkey on 2012-01-13
tried boot-repair and chose the recommended repair and this message appears...

the boot of your pc is in efi mode.
please change it to bios mode.
then try again.


how can i do that?

---

### Post by liquidmonkey on 2012-01-13
a little update,
i have tried the following but was unable to save the grub file so it was a dead end... [http://askubuntu.com/questions/67430/my-fresh-installation-doesnt-load-pulseaudio-problem](http://askubuntu.com/questions/67430/my-fresh-installation-doesnt-load-pulseaudio-problem)

then i tried this...
[http://forum.notebookreview.com/linux-compatibility-software/422736-ubuntu-noob-scan-disk-errors.html](http://forum.notebookreview.com/linux-compatibility-software/422736-ubuntu-noob-scan-disk-errors.html)
and although i was able to scan the disks, there were no errors but then it just took me back to the same error message as in the OP.

:(

---

### Post by liquidmonkey on 2012-01-13
****BANGS HEAD ON DESK*****

so i found the problem.
earlier when i tried to do a backup of an image using clonezilla, i must have had the image destination wrong cause it wrote an image to my current laptop HDD.
this in turn must have completely filled up the HDD and hence, ubuntu had a very hard time booting up.

went in and sudo deleted the file and it booted up just fine!
weird how a full HDD gives this problem but hey, at least its solved!

thanks for the help!

---

