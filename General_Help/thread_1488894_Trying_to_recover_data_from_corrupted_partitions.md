---
title: "Trying to recover data from corrupted partitions"
date: 2010-05-20
forum: General Help
---

### Post by geek_Man on 2010-05-20
Hey all, I've really done it this time. Long story short, I inadvertently started creating a boot disk over an entire 300GB external hard drive. Needless to say, I had all sorts of data saved on there. I stopped it early on in the process by turning off the drive, but I now I don't know how to salvage what's left. Any ideas? Thanks in advance... :mad:

---

### Post by tgalati4 on 2010-05-20
This is a common issue.  It's easy to make this mistake.

You need to proceed carefully.  My turning off the drive, you have interrupted the process, but also made the drive unmountable by linux.

The basic steps are:

Put a valid partition table on the drive. So that now you can mount it.
Don't format the drive.
Get another drive to receive the recovery data.
Use a recent Ubuntu Live CD to boot from and perform the recover.
sudo apt-get install testdisk
man photorec
Basically you are going to ignore the partition data and simply read the data sector-by-sector and let photorec grab all file types that it knows about (hundreds).

It's a painful process, but I've performed a few recoveries this way including my own botched distro installs.

Here's a similar thread with some more details:

[http://ubuntuforums.org/showthread.php?t=1484463](http://ubuntuforums.org/showthread.php?t=1484463)

A typical install is about 3 GB at the front of the disk, so 99% of your data should be intact.  Expect to spend several hours in pain.

---

### Post by geek_Man on 2010-05-20
Well, it's not a distro partition, it's several partitions I have on an external hard drive. Basically, the only thing that changes is that I don't need to use a LiveCD, correct?

---

### Post by tgalati4 on 2010-05-20
Then you can simply install testdisk:

sudo apt-get install testdisk

man testdisk
man photorec

sudo photorec /dev/sde /media/Extra_Large_Disk_to_Receive_Files

Substitute sde for your actual device name for the bad drive.

You will need a large disk to receive the files.

Normally you would run testdisk first to restore the partitions.  But if you did a system install on a data partition, then you have probably mangled the disk beyond repair, so now data recovery is the priority.

---

