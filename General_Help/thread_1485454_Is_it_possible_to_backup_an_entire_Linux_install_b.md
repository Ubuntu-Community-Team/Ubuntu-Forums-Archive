---
title: "Is it possible to backup an entire Linux install by copy/pasting the entire file sys"
date: 2010-05-16
forum: General Help
---

### Post by inquilinekea on 2010-05-16
system?

I know that it isn't possible in Windows since Windows has the registry and background variables that aren't stored on the file system for some reason.

But what about Linux? Are its environment variables stored on the file system? Is there anything that isn't stored on the file system? Is it possible to even backup a software installation by copying the software's directory from one computer to another? If it's not possible, then why not?

---

### Post by nmaster on 2010-05-16
try this: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

i've heard that it doesn't always work, but i've never tried myself.

you could also take a look at remastersys.  you can use it to make an iso of your installation.

---

### Post by inquilinekea on 2010-05-16
How about transferring an entire installation of a program? (which you cant do in windows thanks to the registry).

---

### Post by JC Cheloven on 2010-05-16
Yes you can make a copy of the entire filesystem (different from simply copying files!), and restore that copy in tha same computer (or other with the same exact hardware) at a later time. Things will work as it was at backup time.

I did that a few times using FSArchiver (comes in SystemRescueCD). Also you can use the builtin utility DD for that, if you learn how. The mini distro called Puppy linux comes with a particulary handy interface for this DD utility.

---

### Post by ryan858 on 2010-05-16
> **inquilinekea said:**
> How about transferring an entire installation of a program? (which you cant do in windows thanks to the registry).

Yes, if you copy the libs for that program, and it's dependencies, etc. and the machine you put it on is the same architecture.

Although it's much more practical to just build and install from a source package on whatever machine you want to transfer to.

---

### Post by inquilinekea on 2010-05-16
oh interesting, so the livecd does determine which packages to install based on the architecture of the computer?

---

### Post by JC Cheloven on 2010-05-16
> **inquilinekea said:**
> oh interesting, so the livecd does determine which packages to install based on the architecture of the computer?

What do you exactly want to do??

---

### Post by inquilinekea on 2010-05-16
Well the last question was primarily a question of curiosity.

I'm getting a new hard drive since my old HD is failing. But the distro might not recognize the new HD as the same as the old one.

---

### Post by jerome1232 on 2010-05-16
Easiest solution is to clone your old hard drive to the new one. The new hard drive must be the exact same size or bigger than the old drive. If the new drive is bigger than the old one you will need to expand some partitions or create new ones if you want to claim that extra unused space.

Also aren't there some issues with the partition table if the new drive is bigger than the old drive? Issues like this are why I like lvm.

---

### Post by ryan858 on 2010-05-16
Yes, the Live CD does determine the architecture and installs the packages for the architecture that it detects.

As for transferring to a new HD... You're probably best off just installing a fresh copy of the OS (Ubuntu I'm assuming) and transferring your files to the new one. You can copy you're entire /home/user/ directory into the new one with no problems... There are tutorials on how to do this (and transferring stuff in general). It would probably be easiest to only transfer any unique files (stuff you made yourself and can't download anywhere) to the new installation manually by mounting the old drive in the new installation, and installing any programs all over again, rather than trying to copy them over and reconfigure them... The latter would take quite a lot of time to do correctly.

But for theoretical purposes, it is possible to do. Just not practical, and very time consuming.

---

### Post by srs5694 on 2010-05-16
> **jerome1232 said:**
> Also aren't there some issues with the partition table if the new drive is bigger than the old drive? Issues like this are why I like lvm.

Not if the drive uses the Master Boot Record (MBR) system -- at least, nothing major. The MBR data structures don't include any references to the disk's size, so going from a smaller drive to a larger one doesn't pose any real challenges. The biggest issue is simply that, if you use an extended partition as the last partition on the disk, it'll end where the old drive ended, so to add partitions, either they'll have to be primaries or you'll have to first expand the extended partition, which isn't normally difficult.

If the drive uses the GUID Partition Table (GPT) system, then a raw byte-for-byte copy from one disk to another will end up putting the backup GPT data somewhere in the middle of the new disk, which is the wrong place for it. Both libparted-based tools (GNU Parted, GParted, etc.) and GPT fdisk can fix this quite easily, though. IIRC, libparted does it automatically. GPT fdisk offers a menu option to do it.

[quote=ryan858]As for transferring to a new HD... You're probably best off just  installing a fresh copy of the OS (Ubuntu I'm assuming) and transferring  your files to the new one. You can copy you're entire /home/user/  directory into the new one with no problems...[/quote]

If you don't make many changes to the system (custom software installations, modifications to system-wide configuration files in /etc, and so on), then this approach can make sense. There are plenty of ways to transfer an entire installation, though. A clone with Clonezilla or something like it is one way. Personally, I generally use tar, as described in the link provided by neil.m.master, since that provides a lot of flexibility. (You can change filesystems, alter how many partitions you use, etc.) One caveat: I don't see mention in that link of editing /etc/fstab, which will probably be required after doing a tar-style copy. You've got to adjust the UUIDs and possibly add or delete entries if you change the number of partitions you use. As usual, Linux provides many solutions to this problem, so you can take your pick of solutions.

---

### Post by r m h on 2010-05-17
The tar method (link) mentioned earlier works, but for a bit-by-bit copy, man dd

remember a file can be /dev/sda1 or /dev/hdc3...

dd -if <source file(system)> -of <target file(system)>

---

