---
title: "Flashing Desktop after Login"
date: 2010-03-31
forum: General Help
---

### Post by deviator on 2010-03-31
I just ran memtest86 on my pc to check for any bad ram for a problem i was having and when i restarted ubuntu after the splash screen loads i just have two panels (top and bottom) and they flash rapidly. i can't seem to do anything except ctrl alt del and restart.

i kept trying to press esc to enter safe mode but it keeps bringing me to the splash screen and ubuntu loads up.

i'm currently using a knoppix cd to type this msg.

thoughts?8-[

---

### Post by deviator on 2010-03-31
i tried to mount my main hard drive to see if i could access the data...i'm shocked with what i'm seeing...please tell me it's fixable

Could not mount device.
The reported error was:
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

dmesg gives me

mtrr: type mismatch for fb800000,400000 old: uncachable new: write-combining
mtrr: type mismatch for fb000000,800000 old: uncachable new: write-combining
r8169: eth1: link up
eth1: no IPv6 routers present
r8169: eth1: link up
eth1: no IPv6 routers present
EXT3-fs: hda1: couldn't mount because of unsupported optional features (240).
EFS: 1.0a - [http://aeschi.ch.eu.org/efs/](http://aeschi.ch.eu.org/efs/)
EXT3-fs: hda1: couldn't mount because of unsupported optional features (240).
EXT3-fs: hda1: couldn't mount because of unsupported optional features (240)


:popcorn:


from what i understand my main hard drive which i've been using for a while now is all of a sudden in a format that cannot be mounted...all i did was a memtest >_<

---

### Post by deviator on 2010-03-31
update

when i login now the panels dont flash and they have icons on them, however, there is an error with gnome-clock and some icons have an x on them, also i get the message

The NetworkManager applet could not find some required resources. It cannot continue.

...what the hell just happened?

---

### Post by km0r3 on 2010-03-31
> **deviator said:**
> update

when i login now the panels dont flash and they have icons on them, however, there is an error with gnome-clock and some icons have an x on them, also i get the message

The NetworkManager applet could not find some required resources. It cannot continue.

...what the hell just happened?

Screenshot?

Terminate NetworkManager and run it from the terminal. HINT: nm-applet . Maybe this gives you some useful debug traces.

> ...what the hell just happened? 	
You tell me...

---

### Post by deviator on 2010-03-31
i seem to be having problems with alot of icons as well, i tried a restart and i'm back to the same old flashing panels. i've booted up into a live cd and i'm trying to run fsck but i still encounter the superblock problem...something about ext4 being ****.

you cannot turn me back to windows...i won't go....

---

### Post by deviator on 2010-03-31
i've tried fsck and tune2fs but with no luck. i keep getting the superblock error. it can't find it to run a scan to repair it...i need this data. any other way to save it?

i've tried 2 live cd's so far knoppix and ubuntu


weird, i just changed hda1 to sda1 and the scan initiated...

---

### Post by deviator on 2010-03-31
doesn't seem like anybody has an answer. i was using 8.1 live cd to access the partition that has my stuff on it. is this why i couldn't fsck the drive?

any possible way to retrieve the data?

---

### Post by km0r3 on 2010-03-31
> **deviator said:**
> 
weird, i just changed hda1 to sda1 and the scan initiated...

What happened next?

---

### Post by deviator on 2010-03-31
well it says the filesystem is clean...i then reboot and the flashing is still happening.

i'm starting to wonder if this is a problem with the gnome interface and the fact that i used gksu to ran klam anti virus...that's what i did before the memtest. =/

also, i booted up my usb with karmic koala in it and managed to access the hard drive, so doesnt look like it's a problem there.

i also tried ctrl alt f2 (while the panels are flashing) and tried "debconf gnome-panel" but it seems pretty useless.

---

