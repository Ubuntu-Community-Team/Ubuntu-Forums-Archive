---
title: "My Ubuntu is dead ç_ç"
date: 2011-10-10
forum: General Help
---

### Post by Bromden on 2011-10-10
Hi all i'm getting crazy with my Laptop...yesterday everything was working fine and today Ubuntu 10.10 doesn't want to start...sometimes it reaches the loading screen but it immediately sends me to the "tty1" terminal. I've tried the recovery mode from Grub, and the failsafeX but it's the same...
 
Plz help ç_ç
 
I can see a ParseError on line 37 on section InputDevice in file /usr/share.....wacom...something. Sorry not enough time to read :\

---

### Post by collisionystm on 2011-10-10
> **Bromden said:**
> Hi all i'm getting crazy with my Laptop...yesterday everything was working fine and today Ubuntu 10.10 doesn't want to start...sometimes it reaches the loading screen but it immediately sends me to the "tty1" terminal. I've tried the recovery mode from Grub, and the failsafeX but it's the same...
 
Plz help ç_ç

Do you have an ATI Radeon Card?

---

### Post by Bromden on 2011-10-10
No Nvidia

---

### Post by collisionystm on 2011-10-10
What version of ubuntu?

Try 

sudo service gdm start

or sudo /etc/init.d/gdm start

---

### Post by collisionystm on 2011-10-10
or at the tty1 prompt type

sudo fsck

this will do a disk check and check for file system errors

---

### Post by Bromden on 2011-10-10
Wow very fast reply thank you ^^
I should umount the Filesystem, how to do that?

---

### Post by collisionystm on 2011-10-10
Reboot your computer, right after the bios screen, hold the shift key

you should be at the grub menu

go to recovery mode

run fsck from in there

---

### Post by Bromden on 2011-10-10
Always mounted...i've tried umount /dev/sda1 but t says the device is busy
 
 
Ok "umount -l" probably did the work
 
 
 
Omg it's crazy, now if I still use "umount" it says that sda1 isn't mounted, but with fsck it says that is still mounted...
 
 
 
I'll try to use Gparted on LiveCD...

---

### Post by Bromden on 2011-10-10
I think there is something wrong with Xorg
 
Parse error on line 37 of section InputDevice in file /usr/share/X11/xorg.conf .d/50-wacom.conf
 
      "..." is not a valid keyword in this section
 
(EE) Problem parsing the config file
(EE) Error parsing the config file
 
Fatal server error:
no screens found
 
...................
 
ddxSigGiveUp: closing log
giving up.
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error.

---

### Post by Bromden on 2011-10-10
Ok problem solved....i feel so stupid x_x
 
Yesterday I had added this line in this file:
 
Section "InputDevice"
        ...     
        Option          "TopX"        "100"     
        Option          "TopY"        "200"      
        Option          "BottomX"     "14000"
        Option          "BottomY"     "6000"
        ...
    EndSection 
"/usr/share/X11/xorg.conf .d/50-wacom.conf"
 
It just broke up my xorg configuration....i've solved the problem using "nano" to edit the file and restore it...
 
However thanks for the help! ;)

---

### Post by mörgæs on 2011-10-10
Good, please mark the thread 'solved' using 'thread tools' (not just by editing the title).

---

