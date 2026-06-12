---
title: "WD Passport Issue"
date: 2010-05-11
forum: General Help
---

### Post by LiteDrive on 2010-05-11
I've done a lot of research on this for the past few months, with the ideology that I could do this myself and figure everything out. The problem is that, regardless of how much I've looked up this problem, mine may be a little too specific.

It started when I ended up (only a few months ago) getting a 500gb WD Passport. I was running Ubuntu 9.10, and when I first attached the hard drive everything was working fine. 

Then I wanted to transfer some music files onto my mom's laptop, which - and I'm sure you can guess this - was running Windows XP. 

So, upon booting up the laptop with the hard drive plugged in things seem to be going fine when a FAT32 error pops up and the P.C. thus shuts down. Repeated attempts with repeated methods (which as we all know are typically useless in the world of the P.C.) rendered repeated results. 

****.

So, I try plugging in my WD passport in Ubuntu and get this error.

   [[IMG]http://img257.imageshack.us/img257/3173/screenshotmxt.th.png[/IMG]](http://img257.imageshack.us/i/screenshotmxt.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

After periodic weeks of research, the only two things I know how to do are 

```
Bus 002 Device 004: ID 03f0:2f11 Hewlett-Packard PSC 1200
Bus 002 Device 003: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 002 Device 002: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 1058:070a Western Digital Technologies, Inc. 
Bus 001 Device 007: ID 05ac:1261 Apple, Inc. iPod Classic
Bus 001 Device 005: ID 0a16:2006 Trek Technology (S) PTE, Ltd 
Bus 001 Device 002: ID 050d:905b Belkin Components F5D9050 ver 3 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

AND of course...

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x01a901a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       31093   249750604+   7  HPFS/NTFS
/dev/sda2           31093       60802   238635009    5  Extended
/dev/sda5           31093       60428   235628544   83  Linux
/dev/sda6           60428       60802     3005440   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3fdef109

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 4043 MB, 4043309056 bytes
125 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2c6b7369

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?      249811      488760   925929529+  68  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(116, 100, 32) logical=(249810, 12, 29)
Partition 1 has different physical/logical endings:
     phys=(288, 101, 46) logical=(488759, 81, 59)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?      171637      241182   269488144   79  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(357, 32, 43) logical=(171636, 83, 47)
Partition 2 has different physical/logical endings:
     phys=(0, 13, 10) logical=(241181, 124, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?       69548      249981   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(69547, 2, 18)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(249980, 117, 49)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?      179952      179955       10668+  49  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(87, 1, 0) logical=(179951, 119, 36)
Partition 4 has different physical/logical endings:
     phys=(335, 78, 2) logical=(179954, 88, 44)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
Note: sector size is 4096 (not 512)

Disk /dev/sdd: 79.8 GB, 79824777216 bytes
26 heads, 50 sectors/track, 14991 cylinders
Units = cylinders of 1300 * 4096 = 5324800 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       14992    77953628    b  W95 FAT32
Partition 1 does not start on physical sector boundary.

Disk /dev/sde: 499.4 GB, 499405291520 bytes
255 heads, 63 sectors/track, 60715 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00021968

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60716   487699456    7  HPFS/NTFS
```

Any help at all would be greatly appreciated...

Thank you.

---

### Post by pytheas22 on 2010-05-12
I've seen errors like this before, and they usually are the result of the drive being uncleanly unmounted in Windows.  Even if there are not actual errors with the file system, Ubuntu won't mount it because it knows it was not cleanly unmounted.

So the first thing you should do is run "chkdsk /f" on the drive from a Windows command prompt, in order to make sure that there are in fact not issues with the file system (if there are, let Windows fix them; chkdsk usually actually works, in my experience).

If chkdsk says the drive is clean, you should be able to straighten out the issue by mounting it once manually in Ubuntu, using commands like:
```

sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt/sdb1
```

You will need to replace "sdb1" with the correct parameters for your device; if you don't know how to find these, let me know.

If the device mounts properly from the command line, unmount it using:
```

sudo umount /dev/sdb1
```

(Note that the command is "umount", not "unmount", for reasons I've never understood.)

From then on, Ubuntu should be able to automount the drive properly whenever you plug it in.

---

### Post by efflandt on 2010-05-12
I don't know if you are running on all cylinders, or if different versions of the 500 GB Passport vary some.  This is what mine shows, although, I have 2 partitions, one with bootable 64-bit Lucid:

```
Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       56730   455680000    7  HPFS/NTFS
/dev/sdf2   *       56730       60801    32703008+  83  Linux

Bus 001 Device 003: ID 1058:0705 Western Digital Technologies, Inc.
/dev/sdf2 on /media/2bc50ecc-0d02-4dea-8e7e-a9e3e2e3e0ed type ext3 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdf1 on /media/WD Passport type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

```Notice that the size and cylinders on your sde are different than this or your sda. Did someone bump it while running or unplug it while writing?

Did you try **chkdsk /f** from Windows like it says to do?

I would download Data Lifeguard software from wdc.com and test the drive.  Then if it tests bad, maybe you could get a warranty replacement.

Just curious what sdc is, that looks totally messed up?

---

### Post by LiteDrive on 2010-05-12
Beautiful. Thanks much, I appreciate the help.

Just so you're all aware: while I'm perfectly literate when it comes to computing, my knowledge is amateur at best (or intermediate). As far as Linux in particular, it's very basic.

Again, thanks.

---

### Post by LiteDrive on 2010-05-12
Just one last thing:

I don't know how to find the parameters for it. Could you give me the code/method which does this?

---

### Post by pytheas22 on 2010-05-12
To find the parameters to use for manually mounting the device, you need to figure out which /dev/sdXX name has been assigned to it by udev.  Generally, /dev/sda1 would refer to the first partition of the first disk attached to your computer, /dev/sda2 would refer to the second partition of the first disk, /dev/sdb1 would refer to the first partition of the second disk, and so on.

From the output that you posted in your first post, it looks like udev assigned /dev/sde1 to your Passport, since that's the only device with 500 gigabyte storage capacity and an NTFS file system.  But you should run the command again just in case the assignment has changed, which could happen if you've unplugged the disk since then.

Assuming it is /dev/sde1, you would run these commands to mount it manually:
```

sudo mkdir /mnt/sde1
sudo mount /dev/sde1 /mnt/sde1
```

If you get any errors, please post them here.  Otherwise, if the command succeeds, it should exit silently.

---

### Post by LiteDrive on 2010-05-14
I ran it again on my mom's laptop. As soon as the P.C. discovered the passport, it shut down with a blue screen of death message. So I ran it in safe mode, did "chkdsk /f", rebooted, and the the check ran. Unfortunately, while it seemed to check out, I still can't mount it in windows without the blue the screen.

And then I gave this a go:

```
theopusvision@theopusvision-desktop:~$ sudo mkdir /mnt/sdb1
[sudo] password for theopusvision: 
theopusvision@theopusvision-desktop:~$ sudo mount /dev/sdb1 /mnt/sdb1
mount: special device /dev/sdb1 does not exist
theopusvision@theopusvision-desktop:~$ sudo mkdir /mnt/sde1
theopusvision@theopusvision-desktop:~$ sudo mount /dev/sde1 /mnt/sde1
theopusvision@theopusvision-desktop:~$ sudo mkdir /mnt/sdd1
theopusvision@theopusvision-desktop:~$ sudo mount /dev/sdd1 /mnt/sdd1
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdd1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
theopusvision@theopusvision-desktop:~$
```

Same. ****.

Now that I think about it, the blue screen of death might not have been a FAT32 error; it claimed that it had rendered Windows unsafe, proclaiming I shut off certain options/memory in the bios.

---

### Post by pytheas22 on 2010-05-14
Hmmm, this is strange.  Have you tried connecting it to more than one Windows computer, with the same results?  Did chkdsk detect any problems with the disk, or did it think everything was alright?

Ubuntu has a utility called ntfsfix that may be able to fix the issues with the disk (assuming they are only software issues, and that the hardware itself is still sound).  Native Windows tools should generally be better for a job like this than Linux ones (since NTFS is the native Windows file system), but since you already tried chkdsk unsuccessfully, giving ntfsfix a try can't hurt.

ntfsfix should already be installed by default on Ubuntu 10.04 (if not, search for it in the Software Center), and the syntax is just:
```

sudo ntfsfix /dev/sde1
```

(of course, replace */dev/sde1* as appropriate).

Also, I see from your output above that you were able to mount /dev/sde1 correctly.  This wasn't the Passport, I presume, since you then went on to mount /dev/sdd1 without success?

---

