---
title: "cannot boot, no fstab"
date: 2010-09-05
forum: General Help
---

### Post by lawakeen on 2010-09-05
I have recently re-installed lucid lynx upgrade, so  I backed up my files on a drive that I don't have anymore.  When it was installed I copied the files into the home folder, then put copied them into the premade directories (Documents, Pictures, etc.).  I rebooted and was dropped into busy box. 

I found out there is no fstab file in my /etc.  "find" command turned up no fstab.  I would love to be able to mount my hard drive, this happened before, and I was told that the computer was somehow "mis-aligned" which I interpret to mean that the there was no fstab so the computer couldn't mount the drive.

"ls" shows my five sda partitions.

oh, and i would really love to keep my content if possible

thanks

---

### Post by MooPi on 2010-09-06
Could you boot from a Live CD and create an fstab to correct the problem ? Just a brain stormer of an idea and could be way off. But I'm going to grab my Live CD and test the idea. I just tried my idea and no the temporary fstab is insufficient. But you can run ```
sudo blkid
```from terminal to get the UUID to create an fstab from scratch. Maybe use my fstab as a template to start. 
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b3ce4e2a-f862-4f38-9402-00301e1f52a1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9b447b24-4a29-425c-87c5-4068e5ea50e4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```
Substitute your info into the correct locations and paste into your /etc

---

### Post by Rubi1200 on 2010-09-06
Please boot the computer with the Ubuntu CD in live mode and post the results of the bootscript linked to at the bottom of my post.

The results will tell us more about your setup, including fstab, and make offering solutions easier.

Thanks.

---

### Post by lawakeen on 2010-09-07
I couldn't buy a CDR yesterday because it was labor day, so sorry if I made you wait.

I burned the live cd, using the ubuntu download directions to the letter.
When I booted from the cd the boot failed.  This is what the log said (the info you get when you press escape during boot)--this is hand typed so there may be scribal errors.
> 
(process:328): GLib-WARNING **: getpwuid_r(): failed due to unkown user id (0)
                                                                                                                                              Killed
stdin: error 0
Generating locales...
     en_US.UTF-8...done
Generation complete.
Using CD-ROM mount point /cdrom/
Identifying.. [94079c8e67a3363d5f041a810fd5e3cc-2]
Scanning for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
Found label 'Ubuntu 10.04.1 LTS_Lucid Lynx_ -Release i386 (20100816.1)'
This disc is called:
'Ubuntu 10.04.1 LTS_Lucid Lynx_ -Release i386 (20100816.1)'
Copying package list..gpgv: Signature made Mon Aug 16 10:19:01 2010 UTC using DSA key FBB75451
gpgv: Good signature from  "Ubuntu CD Image Automatic Signing Key <cdimage@ubunutu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this diesc are:
deb cdrom:[Ubuntu 10.04.1 LTS_Lucid Lynx_ -Release i386 (20100816.1)]/ lucid main restricted
Repeat this process for the rest of the CDs in your set.
W: Skipping nonexistant file /cdrom/dists/lucid/main/binary-i386/Packages
W: Skipping nonexistant file /cdrom/dists/lucid/restricted/binary-i386/Pacakges
Killed



After say ten minutes this error message reprints.
bummer.

Also if makes any difference I made to disc using a mac and a cd-rw. 
I tried booting the mac from the cd but couldn't.  I tried to do it by pressing "c" at start-up and later by pressing shift-option-command-delete at start up.  It just spit the disc out and booted normally.

---

