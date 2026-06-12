---
title: "installation on external USB partition"
date: 2011-04-06
forum: General Help
---

### Post by dragonfly41 on 2011-04-06
So far I've used ubuntu 10.10 in dual boot (wubi) demo mode and I now want to install on a logical partition in an external USB drive.

I've got ubuntu-10.10-desktop-i386.iso sitting on my ubuntu desktop ready to burn into the external partition already formatted ext4 and bootable flag set.   See snapshot attached.

I follow the instructions here ..

[http://www.ubuntulinux.org/desktop/get-ubuntu/download](http://www.ubuntulinux.org/desktop/get-ubuntu/download)

to open 

System > Administration > Startup Disk Creator

I select the target external partition where I want to install ubuntu.

However the button "Make Startup Disk" is not in focus and cannot be clicked to burn ubuntu into the partition.

Nor is the text "when starting up from this disk, documents and settings will be: .." with radio buttons in focus.  See the snapshot attached.

The button "Erase Disk" is in focus .. but I'm not sure if this should be clicked first or if it would erase the target partition /deb/sdb3 .. or the entire disk   /dev/sdb

So what step have I missed in basic installation procedure to install into /dev/sdb3 ??

Another puzzle.  Try as I might I cannot attach a label - RECOVERY - to /dev/sdb9.
Why is this?

I'm attaching snapshots of 

[LIST]
[*]the freshly partitioned external USB disk.
[*]startup disk creator
[/LIST]
Thanks.

---

### Post by lithopsian on 2011-04-06
It isn't clear what you're trying to do.  Or perhaps you aren't clear what you need to do?

Burning the iso file to a CD or USB drive is not installing.  This will simply create what is known as a Live CD.  This must be on a different media to where you wish to finally and permanently install Ubuntu.

The Live CD can be booted but it is somewhat slow and you won't be able to make persistent changes to settings (except for a limited set if you select that option and provide the space).  From the Live CD you will be able to make a full installation.  This isn't normally to a USB drive but it can be so long as you are aware of the obvious limitations and dangers.  A Live CD is also a recovery disk for any problems you have later.

If you want to put the iso image on the USB and also do the install to the USB, then you will need to make two different partitions.  The installer will make partitions for you if you want but you'll have to set aside sufficient space.

If you cannot write the iso to a location it is because it needs a blank partition.  The erase button gives you the option of creating an empty partition from an existing partition but obviously anything on the partition will be lost.  Once you have selected a suitable;e blank partition you will get the the options.  I suggest that you create suitable partitions with an external program so that you are confident what you are erasing.

BTW, it is worth pointing out in case you didn't get it from my waffling that you don't put an iso image on an ext4 partition.  An iso image is its own file system and it is written byte for byte onto a blank area of disk.

---

### Post by dragonfly41 on 2011-04-06
After posting I read this ..

[http://ubuntuforums.org/showthread.php?t=1711155](http://ubuntuforums.org/showthread.php?t=1711155)

"i tried the startup disk creator but it does nt work"

"make it simpler use unetbootin available at the software center".

........................................................

Sure enough Unetbootin worked .. whereas Startup Disk Creator didn't !

I still don't know why I can't easily rename partitions but I'm sure I'll find a way.

---

### Post by dragonfly41 on 2011-04-06
Sorry lithopsian .. our messages crossed.

I'm trying to get away from LiveCD and install various OS in an external USB drive where there will be persistence.

Then I'll turn to recovering my internal screwed up Vista (which has dual boot ubuntu (demo mode) at the moment).

Unetbootin seems to have _burned_ the iso into /dev/sdb3  (ext4 format) but I've yet to reboot to test.

---

### Post by lithopsian on 2011-04-06
I still don't think you follow me.  Burning the ISO to a USB drive is not the same as "getting away from a Live CD".  OK, you can configure some persistence but it is still a Live CD.  On a USB drive :)  You will be running a Live CD, with the entire system having to be unpacked each time you boot.  You will not be able to upgrade your system as security updates come out, or install new software, or a great many other things that most people consider important.

It sounds to me like you actually want to install Ubuntu, albeit on an external drive.  Nothing wrong with this, but that involves burning a Live CD (possibly on a USB drive) and then installing from it to where you want Ubuntu.

---

### Post by dragonfly41 on 2011-04-06
Thanks for correcting me.   I agree there are two steps to take.

Burning iso into USB partition.

And then optionally clicking on the tempting "Install Ubuntu 10.10" button on the desktop.

So far for the last few weeks after booting I have avoided that by clicking ESC within 3 seconds of startup and then selecting demo mode which of course loses all sessions.   This approach has been necessary to preserve crashed Vista files and avoiding the internal disk being scrubbed for a ubuntu full installation.   I can recover my windows files.

I now *appea*r to have burned ubuntu into /dev/sdb3 .. I can see it right now as an icon .. one of several mounted external partitions .. on my desktop in ubuntu in windows mode.

but when I select from F12 .. boot from external USB drive .. instead of booting from hard drive .. I can't yet get into this external ubuntu "LiveCD".

============================================================================================

p.s. I've got separate bootable CD's including RIPLinux, Ubuntu_10.10 and Parted Magic .. just to be safe.  An added problem was that I had a failed CD drive but that has been overcome with an external USB CD-DVD drive.

============================================================================================

p.p.s Since I've got ubuntu LiveCD already working (abeit wubi style) .. if I **do** click on the Install Ubuntu 10.10 on my desktop .. can I specify an external partition /dev/sdb3  as target or is it installed in the active partition (in my case Windows).

---

### Post by C.S.Cameron on 2011-04-06
Startup disk creator and UNetbootin only install to FAT and only work on the first partition of the drive.
It looks like you have plenty of space to do a full install.
It is best to disable your internal drive first and use manual partitioning.
You should be able to install to your first ext4 partition.

---

### Post by C.S.Cameron on 2011-04-06
Oops double post.

---

