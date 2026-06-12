---
title: "Can't Read Any Dvd Burnt With Nero In M$ Xp"
date: 2006-05-14
forum: General Help
---

### Post by ahaslam on 2006-05-14
I have recently moved from XP to Linux. After trying several distros, I've settled with Ubuntu as it meets most of my needs and works well straight out of the box.

There is only one problem that is troubling me at the moment: I CAN'T READ ANY DVD THAT WAS BURNT WITH NERO IN XP. I can however read discs created with other burners such as Sonic RecordNow.

This is very fustrating as all of my recent doccuments & music downloads were backed up with NERO before removing M$. 

When I insert one of these discs, Ubuntu automaticly mounts it as usual, but does not open its contents in a new window. When I open it a few plain text/unknown files are shown, their titles just being a long string of ????...

These discs did work in XP, it's weird how it's only the NERO dics that have this problem. I couldn't find existing help on this topic and would really apreciate some guidance. If it's a NERO thing, I'm sure others may of had this problem.

Thanks for reading all that, I hope someone can shed some light on this.

Thanks again,
Tony.

---

### Post by louis_nichols on 2006-05-14
well... things in the dvd area are pretty much standardised, so things should work out eventually. Start by pasting here the output of the command *mount* when you have such a disk in the tray, that you can't read. And also the contents of the file /etc/fstab.

Did you write DVD's under Nero with the iso option, or did you choose udf? Did you change the default filesystem properties? Like maximum number of characters in filename and all that stuff.

---

### Post by ahaslam on 2006-05-14
Thanks for your fast response.

I inserted one of my discs, it auto mounted and as I was entering the terminal a window opeded with the proper disc contents! This was one of the NERO discs that I tried earlier and didn't work!

The only thing that I've done between posts is reboot. I've rebooted again to ensure it's not a fluke, it still works! I've successfully transfered mp3's from a NERO backup DVD to my USB MP3 player, so I guess all is fine?

Very weird that for weeks only NERO discs didn't work and now they do after doing nothing. 

Does Ubuntu automaticly fix itself when fustration reaches a certain level? I wish my Unichrome Pro graphics worked with hardware acceleration!

Thanks again,
Tony.

---

### Post by louis_nichols on 2006-05-14
Glad to read it works. Some things can happen rather unpredictably. Perhaps some are darn right normal, but I'm not experienced enough to understand all that stuff myself. It may be Linux, but it is also true that there are times when a reboot fixes stuff.

---

### Post by ahaslam on 2006-05-14
A bit temperamental - just stoped working - rebooted again & ok, but for how long?

Here's th info you requested earlier:

ahaslam@ubuntu:~$ mount
/dev/hda1 on / type reiserfs (rw,notail)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
/dev/hda3 on /media/hda3 type reiserfs (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=ahaslam)
/dev/sda on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8)
ahaslam@ubuntu:~$


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               reiserfs notail          0       1
/dev/hda3       /media/hda3     reiserfs defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by ahaslam on 2006-05-14
Something I've noticed...

When I boot without my USB MP3 player attached all is fine. When I attatch it while the computer is running everything seems to work, but transfers to USB get slower the longer it's connected. If I boot with the MP3 player attatched, the device works consistantly well, cds/dvds mount, but those burnt with NERO don't work (the contents are garbage).

Could this be a conflict with my USB MP3 player?

Thanks again,
Tony.

---

### Post by louis_nichols on 2006-05-14
Temperamental indeed. Let me guess: it started acting weird again after you enterd a DVD not written in nero and then one written in nero, at which point it stopped working right.

Now, to me, this qualifies as a bug, but It's quite likely just a setting in mounting the iso filesystem. So....the options for mounting iso9660 are seen on the mount manpage:

man mount

but, as I can't replicate your situation, I can't test what exactly should be used, unfortunatelly. I suggest you try experimenting with the different options relating to iso9660... Another thing is that your dvd's might be in udf format, in which case you should try unmounting one and then manually mounting it with

sudo mount -t udf /dev/hdc /media/cdrom0

---

### Post by louis_nichols on 2006-05-14
[QUOTE=Anthony Haslam]Something I've noticed...

When I boot without my USB MP3 player attached all is fine. When I attatch it while the computer is running everything seems to work, but transfers to USB get slower the longer it's connected. If I boot with the MP3 player attatched, the device works consistantly well, cds/dvds mount, but those burnt with NERO don't work (the contents are garbage).

Could this be a conflict with my USB MP3 player?

Thanks again,
Tony.[/QUOTE]
It might be. Not a normal one, but unexpected interactions can exist. I've encountered similar situations too.

---

### Post by ahaslam on 2006-05-14
It's certainly got something to do with my USB MP3 player.
When a disk doesn't work, manually mounting it doesn't help. If I remove both USB & DVD, re-insert the DVD, it *MAY* work. I can then connect my MP3 player and transfer files (very slowly, but it works).

...Temperamental but these dvd's didn't work **AT ALL** in other distro's. I haven't gained any of the problems that occured with M$, so I'll put up with temperamental NERO discs for a while. When they decide to work, I'll copy their contents to my hard disk and burn new backups with K3B. Shouldn't have  any trouble then!

Thanks for your help, it was greatly appreciated,
Tony.

---

