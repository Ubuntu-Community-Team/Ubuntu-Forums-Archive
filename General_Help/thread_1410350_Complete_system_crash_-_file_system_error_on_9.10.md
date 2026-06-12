---
title: "Complete system crash - file system error on 9.10"
date: 2010-02-18
forum: General Help
---

### Post by Nato99 on 2010-02-18
I've been running 9.10 on my laptop for a couple of months with absolutely no problems. Down loading the recommended system updates regularily and mostly just internet and game use. After booting up last week the package manager showed a red circle and indicated that it was not able to contact the server even though I was still able to get on the internet. I rebooted and during the title screen it started down a file system check with got to about 43% and then hit an error and kicked me out to a terminal prompt.
After running "fsck" two or three times it finally booted into the normal GUI however once I was there nothing would open.
I double click on an icon and it looks like it might start the application but then it just gives up. 
Also, everytime I boot up now I have to run fsck serveral times just to get it to boot all the way to the GUI.

I've tried to reinstall 9.10 from a CD but it stalls out as well. I have been sucessful getting s live copy of SLAX to load.

Any help would be very much appreciated.

Thanks

---

### Post by ajgreeny on 2010-02-18
Try booting to recovery mode from grub and then run ```
apt-get update
``` and ```
apt-get upgrade
``` one at a time.  In recovery mode there should be no need for sudo.

That may help sort out the problem, but if not try running a manual fsck from the live CD, with ```
sudo fsck /dev/sdx#
``` using the correct dev name for your root partition.

---

### Post by Nato99 on 2010-02-28
Thanks ajgreeny

Did the update and upgrade but still no good. I can get around in text mode just fine but the system crashes when i try to load the GUI.

Is there a way to "nuke" the system and do a fresh install?

I've tried doing an install from the CD but the system crashes as soon as it gets to the splash screen.

---

### Post by Nato99 on 2010-03-02
Rather than trying to "nuke" the whole thing, is there a way to repair the file system using the live CD? 
When i do a FSCK in text mode it comes back clean. I can navigate around in text mode with no problems. All the issues start when i try to enter the GDM or boot to the GUI.

---

### Post by amrypma on 2010-03-02
Do you have any log files? should be in /var/log/ somewhere.

---

### Post by rnerwein on 2010-03-02
hi
the logfile you have to look are: /var/log/messages, /var/log/syslog, /var/log/kern.log and /var/log/daemon.log.
but i guess your problem comes from your graphic card. i think you ain't using the native driver which comes with ubuntu and you did a update including a new kernel. have a look in your 
~/.xsession-errors. if you have a special driver - reinsall it. you even can try:
cd /etc/X11
mv xorg.conf xorg.conf.blablu
and try to reboot. then the system will try to come up with the native driver.
i don't know if this work for you, but the way i'll try it ( did it once and it worked - nvidia graphic )
installed the nvidia driver again - every thing was ok.
good luck
ciao

---

