---
title: "USB Extrernal drive not mounted"
date: 2010-08-17
forum: General Help
---

### Post by kharat on 2010-08-17
In HH, I had formatted an external drive in April 2010 and was using it till yesterday, without any problem. I first time plugged this drive to windows yesterday, and after that this drive does not get recognized ( as /dev/sdb in the past) and does not get mounted.

fdisk output doestnot return anything.
lsusb does not show the drive.

new formatting cannot be done until /dev/sdb gets recognized.

guide appropriately.
vikas..

---

### Post by Unterseeboot_234 on 2010-08-17
I have been fighting this also. It is a combination of hardware and OS. If you have been using Win XP, a Linux-formatted hard drive is not recognized on the XP box. If your XP formatted and copied some files before you hooked the external HD to the Linux box, then Linux ignores whatever XP stored in the temp files and can see NTFS and FAT32 partitions.

That external USB-drive will read/write on Windows 7. Something gets written to the drive and Ubuntu then has a 'name' that will mount the drive. On my machine the name is something like '8C4472B54472A19E' (but that names changes with usage.) My Firewire external is always the name I gave it, eg. 'L'.

I have an adapter plug to convert IDE / SATA connector to USB. If the hard drive was made BEFORE 2001 I have to use Win XP to use the hard drive as an external USB with this adapter. The adapter was supposed to work in Vista, it does not. The adapter will not work in Windows 7. It does work with NT (because XP is NT with a desktop). The adapter will work with the mfg CD driver installation. If the drive was made after 2001, the adapter will work with Vista, but not Windows 7.

I have searched the web, at some point when the USB connection is discovered a name is generated for the device that echos to Linux. Without that echoed name, Linux cannot assign sdb(...c..d...e..f,etc.). You have to get past this point to get administrative terminal to give results -- that is: fstab, lsusb, and so on.

Since everything on Linux is a file, I seek if there is any answer to fake a device name? If my adapter plug works on Win-NT, why won't it work on Linux?

---

### Post by Unterseeboot_234 on 2010-08-18
I have unplugged and plugged in a variety of hard drives including: external storage drives ( the drive is enclosed in a factory box with its own power supply ). And the adapter kit that bridges old IDE internal hard drives and makes them USB pluggables. And also opened an old XP computer to use the internal power plug and IDE cable.

If the drive is one partition created with any OS, then USB will see and automount 99 times out of 100 and put a disc icon on your desktop. If the drive has multiple partitions the results will depend on which OS made those partitions and also if the drive was a Master or a Slave jumper. If the drive was CS (cable select) you will have variable results.

Using Ubuntu's System->Administration->Disk Utility ( see the attached screen shot ). This is a formerly internal 250-gig Samsung that was formatted with PartitionMagic and used in an XP box with 3 partitions. Long story short, the partition tables are Windows shortcuts.

Ubuntu sees the device but not the partitions. Doing a manual mount:
[**[COLOR="RoyalBlue"]Manual mount community documentation[/COLOR]**]("https://help.ubuntu.com/community/Mount/USB")
and I get back an error message: 'we are missing a partition table or helper program'. Windows XP or NT does mount the same drive with the adapter-to-USB. To go back to Linux and try to read the same drive will take programming to get the files, or I can format the drive using gParted to gain a universal pluggable-USB hard drive.

If a drive has hardware problems that will confuse any partition table scenario. In my pile of computer junk I have seven old hard drives. Some of them will never hold data again. One of the drives was formatted with NT4.0 back in 1993, a 250-MEG. That drive works for every configuration I have tried: Master, Slave, USB.

The adapter has worked out well. I have gained a 40-gig, a 250-meg, and a 250-gig USB as portable storage. I can verify and format media very quickly. I had forgotten I had SCSI drives in that mess. I couldn't find any SCSI cables and ended up throwing those drives away.

So, Windows chkdsk might repair a partition table if Windows made that partition and the drive is installed in a computer cabinet. RescueCD and other programs have always wasted my time with no good results, except .jpeg. Forensics on a hard drive requires evaluating the history of the partition(s). It is easy to get data from a hard drive, but the OS won't know the TYPE of those files.

I'm no expert. The above is just my trial and error(s).

---

