---
title: "stuck at intramfs/busybox. how to backup files?"
date: 2010-10-20
forum: General Help
---

### Post by Whik on 2010-10-20
hello, i find myself in a situation very similar to here. 
[http://ubuntu-ky.ubuntuforums.org/forumdisplay.php?f=331](http://ubuntu-ky.ubuntuforums.org/forumdisplay.php?f=331)

when i try use boot a live disk off my flash drive, it gives me the same issue. 

right now, i was just wondering how i would be able to get all my files off of my hard drive and onto an external drive so i may just format and reinstall everything on my computer.

any tips on how to do a simple copy over through the busybox or intramfs?

---

### Post by Whik on 2010-10-20
anyone have any idea of how to do a simple copy command? could i just type like 

copy (hd0,1) to whatever the hard drive shows as?

---

### Post by fat tubby on 2010-10-20
copy and paste

---

### Post by Whik on 2010-10-20
ya know....if it was possible to do that...i would have.

---

### Post by Whik on 2010-10-20
managed to get up a live disk and its showing my drive with files on it as un mountable and busy. does that help give any info?

---

### Post by bonixavier on 2010-10-20
I'm not sure if I understand your problem correctly. Does your PC boot directly to ash? If you're able to boot into live mode and have the external hard-drive ready, it should be possible to just copy all you have onto it via Nautilus or dd. Please, clarify what your problem is.

---

### Post by Whik on 2010-10-20
okay. so, when i start my computer ill go to the GRUB menu, even if i try to use recovery mode, ubuntu only loads the intramfs/busy box. finally i was able to get a live disk to boot via usb *im using a netbook* and my goal is to just get my music and pictures off the drive on to an external drive so i can format everything and reinstall. on te live disk, when i try to mount the drive to access it i am told that it is busy and theres already a pending operation. same thing happens when i try to mount it with gparted. and in disk utility when i try to check and repair i keep getting a message saying *deamon inhibited* 

is that any better? right now im just trying to get my personal files off of it

---

### Post by Whik on 2010-10-21
bump for justice.

---

### Post by Presence on 2010-10-25
Have you fixed this? If not I've found a solution to the problem, though I'm not quite sure how. I started looking for ways to access the ext4 partition in windows, and found 2 programs: Raise Data Recovery for ext4 and Stellar Phoenix Data Recovery for Linux. I tried the trial version of both and was able to access the data, but couldn't copy any of it as it was a trial version. 

While I was trying to find a free alternative, I booted the HDD back into Linux (used RIPLinux but a LiveCD should have worked) and I was able to mount and see the files. Unmounted the partition and ran fsck without problems. It's now working fine. Not sure if the windows programs I tried fixed something, but it's worth a try.

---

