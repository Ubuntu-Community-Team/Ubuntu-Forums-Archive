---
title: "How can I unmount Swap and Extended on the Ubuntu 5.10 Live Cd"
date: 2006-03-26
forum: General Help
---

### Post by cheetahman on 2006-03-26
I am using GParted and the only way to resize the partitions is to turn off swap and turn off extended since ext3 is inside the extended and so is swap.The one I want to resize is ext3

---

### Post by plors on 2006-03-27
i think it's better if you use the [gparted livecd]("http://gparted.sourceforge.net/livecd.php"), that way you won't have to worry about mounted partitions and you're sure you have the latest software.

---

### Post by cheetahman on 2006-03-27
I downloaded and tried the GParted Live Cd but it doesn't boot all the way on my computer.

Here is some more information

All partitions become unmounted after doing that command I can click on ext3 and resize it and it does it but completes it but the partition is still not resized 

Status:Not Mounted
Size:14747
Used:7766
Unused:6981
Path:/dev/hda6

Should I download the Ubuntu Beta Live cd and used that instead

---

### Post by plors on 2006-03-27
[QUOTE=cheetahman]I downloaded and tried the GParted Live Cd but it doesn't boot all the way on my computer.
[/QUOTE]

sounds like a bug, please let the developers know about this. Filing a bug will only take a minute. [http://gparted.sourceforge.net/bugs.php]("http://gparted.sourceforge.net/bugs.php")

thanks!

(btw, a new version of the gparted livecd has just been released, you could try this one before filing a bug)

---

### Post by cheetahman on 2006-03-27
They are developing it fast and I'll download the new cd and test it to see if it works then test the bugs I found which I think there are two the startup issue and the resolution becoming low. 

Also why would GParted resize the partition but not complete it?

---

### Post by plors on 2006-03-27
[QUOTE=cheetahman]
Also why would GParted resize the partition but not complete it?[/QUOTE]

Newer version of gparted have advanced progressfeedback which should help you to pinpoint te location of the error (and hence help you to find a solution).

---

### Post by jerrykenny on 2006-03-27
The command to turn off swap is 

swapoff /dev/hd?  (dependant on your partitoning)

Depending on whether you have root privelidges you might to 

sudo swapoff /dev/hd?

---

### Post by cheetahman on 2006-03-27
Yes that turns swap off and I am able to resize it but it doesn't complete it.Also could this be what you are refering to 

"LinuxQuestions.Org with the same topic"Also post the output of the fdisk i.e. fdisk -l (via xterm as root)
Resizing depends hda6 will be dependent on the size of the extended and any other logical partitions."

So GParted in the Ubuntu Cd is very out of date and should be using the beta of 6.04 or the GParted cd or what other distros have GParted

---

### Post by cheetahman on 2006-03-27
27 March 2006 : GParted LiveCD 0.2.2-6

Some more major work under the hood.

Fixed some bugs in the new udev set-up.
Cleaned-up Fluxbox a little bit.
Added some more options to Xvesa.
Removed some more unused scripts and files.
Recompiled all programs with better optimizations.
Recompiled most libs to remove static libraries.
The new iso is only 22.5 MB!

Upgraded to: atk-1.10.3, glib-2.8.6, glibmm-2.8.4, glitz-0.5.3, gtk+-2.8.12,
gtkmm-2.8.3, libsigc++-2.0.17, pango-1.10.3, freetype-2.1.10,
syslinux-3.20-pre7, squashfs3.0, expat-1.95.8, libusb-0.1.12,
Linux-2.6.15.5, jfsutils-1.1.10

---

### Post by cheetahman on 2006-03-28
Both System Rescue Cd and GParted Live Cd fail after
-ide-floppy driver 0.99.newide

Resize function doesn't appear in QTParted on Knoppix or any other QTParted program on live cd

Should I download Ubuntu Beta Live Cd since will have an upgraded version

---

### Post by jerrykenny on 2006-03-28
Guess it might not be a bad idea just to back up all your data, and use fdisk or cfdisk to remake your partition table ? . . . you might have further problems with a corrupted partiton table if it's not going too smoothly.

---

