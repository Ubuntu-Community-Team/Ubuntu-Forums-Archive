---
title: "Partitioning Drive"
date: 2012-08-29
forum: General Help
---

### Post by HoCo xXSamXx on 2012-08-29
Hello! I am having ALOT of trouble partitioning my harddrive on my laptop. I am using GParted, and all the options are greyed out! I cant resise or do anything, exept unmount. And when I do try to unmount I get this:
> The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually.

Please, any help will be much appreciated!

---

### Post by nothingspecial on 2012-08-29
Looks like you are trying to partition the one you are using.

You will need to do it from a live cd/usb because you cannot partition a mounted drive.

---

### Post by HoCo xXSamXx on 2012-08-29
Ah, thanks :/ I know I have done it on windows 7 though. Anyways, do you know if the windows 7 install disk, gives you the option to partition?

---

### Post by nothingspecial on 2012-08-30
> **HoCo xXSamXx said:**
> Ah, thanks :/ I know I have done it on windows 7 though. Anyways, do you know if the windows 7 install disk, gives you the option to partition?

I have no idea but any of the Ubuntu downloads come with a partitioner which you are free to download and use.

---

### Post by drmrgd on 2012-08-30
> **HoCo xXSamXx said:**
> Ah, thanks :/ I know I have done it on windows 7 though. Anyways, do you know if the windows 7 install disk, gives you the option to partition?

Are you intending on re-partitioning a Linux drive or a Windows drive?  If you're partitioning a Linux drive, then it's best to not use Windows to do it.  Instead, either boot from an Ubuntu live CD / USB, or make a GParted Live CD / USB to do it.  You can find the GParted live CD installation here:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by mikechant on 2012-08-30
If you are going to resize a Windows partition, you should use Windows, otherwise for creating, resizing, deleting Linux partitions use a LiveCD/USB and Gparted as advised above.

---

### Post by Mark Phelps on 2012-08-30
Sorry if I'm presuming the wrong thing here, but my guess is that you're doing the partitioning because you want to install Ubuntu on a laptop that already has Ubuntu -- and -- you want to retain Win7 in a dual-boot setup.

If those are true, then please read what I've written below; otherwise, sorry for presuming the wrong thing:

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by rickm1945 on 2012-08-30
Mark Phelps' answer is correct I just want to and as per my experience in partitioning. My HP Laptop's HD was setup at the factory as a Dynamic Disk and had Four Primary partitions. I had to buy  disk partitioning software or try to find a free partitioning software that will allow you to convert the dynamic Drive to a basic drive. I used EaseUS, 

[http://www.partition-tool.com/professional.htm](http://www.partition-tool.com/professional.htm).

You will have to use this software in Windows and shrink your Drive to make free space. Then you can use your Ubuntu Live DVD and run the setup. Ubuntu will see the free space then you just add each partition and then install. I hope this helped.

---

### Post by HoCo xXSamXx on 2012-08-30
Thanks for all the replies! I burned Gparted to a CD and used that to craste a partition. And Phelps, I have Ubuntu and want to dual boot ti with windows 7.

---

