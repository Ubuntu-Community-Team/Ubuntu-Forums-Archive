---
title: "Error with GParted."
date: 2009-10-28
forum: General Help
---

### Post by Brain Fire on 2009-10-28
So I was shrinking a partition and after about an hour of it going to work it gave me an error message and had to quit. I rebooted and the grub menu came up like normal. I selected the partition I was working on and appeared to boot normally. With the Ubuntu logo going like normal and when it reached about 1/4 the way it spazes out and goes to an ACSII screen printing stuff out faster than I can read it. It comes to a stop and I've transcribed what was on the screen here:

```
* Setting kernel variable [/ect/sysctl.d/10-network-sec.conf] [ ok ]
* Setting kernel variable [/ect/sysctl.d/30-wine.conf]...     [ ok ]
* Activating swap
* checking root file system
133
Fsck 1.41.4 (27-Jan-2009)
/dev/sda5: The file system size (according to the superblock) is 8319654 blocks
The physical size of the device is 7008356 blocks.
Either the superblock or the partition table is likely to be corrupt!


/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
         (i.e., without -a or -p option)
fsck died with exit status 4
                                                              [ [COLOR="Red"]fail[/COLOR] ]
[COLOR="Red"]*[/COLOR] An automatic file system check (fsck) of the root file system failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the root file system mounted in read-only mode.
[COLOR="Orange"]*[/COLOR] The root file system is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL - D to terminate the maintenance shell and restart the system.
bash: no job control in this shell.
root@steven-desktop:~#

```

How do I run a file system check?

When I run an Ubuntu live cd, I can basically access the files on the troubled partition. I even tried copying them out but apparently some files have both a "no write" and "no read" emblem.

It is running the EXT4 file system.

Thanks!

---

### Post by TeoBigusGeekus on 2009-10-28
When Ubuntu exits at command prompt, type
```
sudo fsck /dev/sda5
```

---

### Post by Brain Fire on 2009-10-28
I used the terminal on the live cd:

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
The filesystem size (according to the superblock) is 8319654 blocks
The physical size of the device is 7008356 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? no

/dev/sda5 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Error reading block 7340032 (Invalid argument) while reading inode and block bitmaps.  Ignore error<y>? yes

Force rewrite<y>? no

Error reading block 7864320 (Invalid argument) while reading inode and block bitmaps.  Ignore error<y>? no

fsck.ext4: Can't read an block bitmap while retrying to read bitmaps for /dev/sda5
e2fsck: aborted
ubuntu@ubuntu:~$ 

```

Should I force the rewrite?

---

### Post by Brain Fire on 2009-10-29
I'd be just as happy copying the data out and reinstalling. But some of the files are marked as "No Read" and why does it appear to happen to specific file types? Is there some way I could mount with the password? Thanks!

---

### Post by Brain Fire on 2009-10-29
Force Rewrite?

---

### Post by Brain Fire on 2009-10-29
Any suggestions?

---

### Post by Brain Fire on 2009-10-30
Is everyone distracted by the new release?

---

### Post by akakingess on 2009-10-30
They probably are distracted, but I'm at work, so I couldn't care less about Karmic until I get home :)  I would try using sudo cp to copy the necessary files, although, really you should just be concerned with your "home" directory, which you should have access to copy, as that saves all of your settings and such, but you MAY have to reinstall some software that is loaded into the root directory (file system). However, your personal settings for those programs (software) should still be stored within your home directory, just be sure that you copy the hidden files as well, I'm not sure how to do that but you should be able to figure it out with "man cp" or "man ls" while viewing your home directory.  I am no expert, but trying to help you out, sounds like you're in a pinch, and everyone else is a little distracted today and probably for the next week or so, unless it pertains to Karmic.

---

### Post by HardcoreSSG on 2009-10-30
> **Brain Fire said:**
> Is everyone distracted by the new release?

Yeah I'd have to agree we're all distracted now! Ever since Karmic has been out, we all have problems of our own! LOL!:D

---

### Post by Brain Fire on 2009-10-30
Yes, it's a pretty bad time to break down. :(

So I'm trying to access the files via the live cd of Ubuntu so the fact that I'm having permission problems should be the same for everyone if you tried to access your files with the live cd. but what I don't understand is why is it seemingly random that some files have the X emblem but not others. Were those the files that GParted were moving when it stopped abruptly? Are they corrupt? How many files does GParted move at once? Thanks.

---

### Post by Brain Fire on 2009-10-30
Ok so I copied all of the files that I had permissions for. Does anybody know how I could get those other files that I need permissions for? Is there anywhere I can plug-in my password to get access or should I just go with the force-rewrite that fsck suggests? What sort of damage should I expect from it? I'm going to have to format the entire disk anyway so I'm going to try it one way or another.

---

### Post by Brain Fire on 2009-10-31
What is a rewrite anyway?

---

### Post by Brain Fire on 2009-11-01
Do you think a file system check will fix this?

---

### Post by Brain Fire on 2009-11-02
All I need is for someone to tell me that it is impossible to get my files via the live cd. Which is ridiculous because when it tells you you don't have permission, it should prompt you to enter your password so that you can have access to them. I tried entering username and password at the login screen on the live cd but it said it didn't recognize me. I'm not too surprised but it was worth a shot. Thanks.

---

### Post by P4man on 2009-11-02
> **Brain Fire said:**
> All I need is for someone to tell me that it is impossible to get my files via the live cd. Which is ridiculous because when it tells you you don't have permission, it should prompt you to enter your password so that you can have access to them. I tried entering username and password at the login screen on the live cd but it said it didn't recognize me. I'm not too surprised but it was worth a shot. Thanks.

dont enter a password just hit enter. Livecd's password is blank.

---

### Post by Brain Fire on 2009-11-02
> **P4man said:**
> dont enter a password just hit enter. Livecd's password is blank.

I know. Trying to copy my files using the live cd didn't work because it kept telling me that I didn't have permission. So in a fit of desperation I tried putting my username and pass at the login screen to show the computer that I'm the owner of the files and to quit bothering me with the "permissions" issue. The only way I know how access the files is selecting the partition at the grub menu and booting like normal. But since that isn't an option for me I need an alternative way to get my files. Being able to login at the live cd menu would be great but that doesn't work. So, if I can't get around the permissions issue when using the live cd then that means that I have no choice but to reinstall and lose what files I couldn't salvage. Right? I'll try the "force rewrite" thing but I want that to be last-resort just in case it makes things worse. Thanks.

---

### Post by P4man on 2009-11-02
> **Brain Fire said:**
> I know. Trying to copy my files using the live cd didn't work because it kept telling me that I didn't have permission. So in a fit of desperation I tried putting my username and pass at the login screen to show the computer that I'm the owner of the files and to quit bothering me with the "permissions" issue. The only way I know how access the files is selecting the partition at the grub menu and booting like normal. But since that isn't an option for me I need an alternative way to get my files. Being able to login at the live cd menu would be great but that doesn't work. So, if I can't get around the permissions issue when using the live cd then that means that I have no choice but to reinstall and lose what files I couldn't salvage. Right? I'll try the "force rewrite" thing but I want that to be last-resort just in case it makes things worse. Thanks.

Open a root filemanager

```
gksudo nautilus
```

Use that to browse to your harddisk (/mnt/nameofharddisk). That should let copy files.

---

### Post by arepaking on 2009-11-02
Brain Fire,
I would do this:

Boot from the Live CD and backup your files using gksudo to an external hard drive or USB flash drive, then reinstall Ubuntu by reformatting your partition. I can guarantee you that you will have peace of mind knowing that your system has been defaulted to the final release of Ubuntu Karmic.

Good luck buddy!

---

### Post by seeker5528 on 2009-11-02
If you have a way to make a CD, my first preference in this situation would be to download System Rescue CD:

[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

: boot from that, make a mount point, mount a known good parition, replacing sdX with the actual device names in the examples below:

mkdir /mnt/ubuntu
mount /dev/sdX /mnt/ubuntu

: then run testdisk:

testdisk /dev/sdX

: scan for partitions, since you were in the middle of resizing the partition you might also want to do the deep scan, once the scan has completed you should have the option to select a partition and view the files, when viewing the files you should have an option to copy files, when you choose to copy files you should be able to browse to /mnt/ubuntu to set that as the location to copy files to, if you did not choose to copy all the files, additional copy operations will defalut to the location you previously selected as the target location.

Also if you can connect to the net while running from the Ubuntu CD, you should be able to open a terminal window and type:

apt-get update
apt-get install testdisk

: if you need to. I think the testdisk in Jaunty was new enough to provide the copy option for ext3, the one in Karmic should definitely be new enough.

If you were able to copy files with testdisk and the files seem to be OK then you can delete the partition and create a new one.

I have not had the situations come up where I have had to do recovery on partitions other than NTFS or FAT, so not sure about the usage of other tools in case testdisk doesn't get good results. Photorec, which is part of the testdisk package, is one option, but the couple of times I have used it, results were mixed because it can only salvage files that are saved in contiguous blocks on the hard drive, the larger the file the higher the probability that you will only get part of it. 

Later, Seeker

---

### Post by Brain Fire on 2009-11-02
I'm having trouble simply downloading the ISO. On this computer, I'm using windows. I diligently read the help page and checked the forums but I can't seem to get wget to download the ISO.

---

### Post by P4man on 2009-11-03
> **Brain Fire said:**
> I'm having trouble simply downloading the ISO. On this computer, I'm using windows. I diligently read the help page and checked the forums but I can't seem to get wget to download the ISO.

Then dont use wget. Just download it here:
[http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/1.3.1/](http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/1.3.1/)

---

### Post by Brain Fire on 2009-11-03
Ok so I did a deep scan of the partition and it basically said that the entire thing couldn't be recovered. I wasn't given the option to copy files. I then did the scan on a ntfs partition where it did give me the option to copy files so I know I wasn't missing something the first time.

This is basically what it said:

```
The following partitions can't be recovered
       start      end           size in sectors
EXT4   0 0 1      4142 253 63   66557232
```

66557232 = 31.74 GB which is essentially the entire partition.
What does this mean?

---

### Post by seeker5528 on 2009-11-04
> **Brain Fire said:**
> 
66557232 = 31.74 GB which is essentially the entire partition.
What does this mean?

That's not looking good to me. Gpart is another utility the tries to find partitions.

[http://www.brzitwa.de/mb/gpart/](http://www.brzitwa.de/mb/gpart/)

Other than that it sounds to me like you will have to try your luck with some utilities that can scan the raw data and try to pick the files out.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://linux.die.net/man/1/foremost](http://linux.die.net/man/1/foremost)
[http://www.student.dtu.dk/~s042078/magicrescue/manpage.html](http://www.student.dtu.dk/~s042078/magicrescue/manpage.html)

I have used photorec with limited results, have not used foremost or magicrescue. 

All of these are included on System Rescue CD. 

R-Studio seems to do good with NTFS/FAT and looks like they have an R-Linux available at no charge:

[http://www.data-recovery-software.net/Linux_Recovery.shtml](http://www.data-recovery-software.net/Linux_Recovery.shtml)

: but it's not a Linux program just handles the Linux file systems, so you need Windows to run it.

EDIT: After reading the beginning of the thread again.....

I see that you did do an fsck on there and when asked about forcing a re-write you said no. Not sure, if you say yes to this, if this will leave you any better relative to reading the files you couldn't read, but may be worth trying. Might at least get the partition useable again with most of the files, the ones you can't read at present you might just have to write off. 

Later, Seeker

---

### Post by Brain Fire on 2009-11-06
Ok, I'll try these. If all-else fails then I'll try the rewrite and if that fails then I'll just have to cut my losses.

So thanks to everyone for their help and patience! :)

---

