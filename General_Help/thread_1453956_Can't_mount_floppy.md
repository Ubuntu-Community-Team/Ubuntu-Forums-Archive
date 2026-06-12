---
title: "Can't mount floppy"
date: 2010-04-14
forum: General Help
---

### Post by HiSiskin on 2010-04-14
fsck /dev/fd0
does work properly with no error, emitting correct data on files on the fd. However,

sudo mount -t msdos /dev/fd0 /media/floppy0

nor Palimpset GUI tool don't work for the fd disk. The GUI tool says "media not detected." The mount command doesn't emit error, it just normally(?) ends with silence indicating something which I do not understand. The floppy doesn't get mounted.

/etc/fstab has the entry:
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

What could be the cause and the solution for my poor little floppy disk problem?

Thanks in advance.
p.s. I have renewed the floppy drive hardware but the problem continues.

---

### Post by hryanjones on 2010-04-14
This may not be much help, but I've had problems in the semi-distant past using floppies w/ Ubuntu.  I remember that downloading more packages (which aren't included by default as floppies are, shall we say? out of style) was the way to go.  Looking at available packages **fdutils** sounds a bit familiar.

Good luck.

---

### Post by HiSiskin on 2010-04-14
> **hryanjones said:**
> This may not be much help, but I've had problems in the semi-distant past using floppies w/ Ubuntu.  I remember that downloading more packages (which aren't included by default as floppies are, shall we say? out of style) was the way to go.  Looking at available packages **fdutils** sounds a bit familiar.

Good luck.
Thanks. I did what you suggested:

apt-get install fdutils

Installing was OK but the floppy problem wasn't solved. Fsck works for the fd but the mount command and the Palimpsest tool don't do things as expected.

---

### Post by HiSiskin on 2010-04-14
:confused:Oddly enough, after commenting out the /dev/fd0 entry on the /etc/fstab, and reboot, I can mount/umount the floppy normally from the command line, and an fd icon can be seen on the desktop.  The Palimpsest GUI tool still says 'media not detected', though.

All the files on the floppy belong to the 'root', not to the user, so we need to copy them onto a user directory for editing them.

I don't see the reason for this weird behavior regarding the small fstab entry. Could anyone teach?

---

### Post by mycroft34 on 2010-04-15
> **HiSiskin said:**
> :confused:Oddly enough, after commenting out the /dev/fd0 entry on the /etc/fstab, and reboot, I can mount/umount the floppy normally from the command line, and an fd icon can be seen on the desktop.  The Palimpsest GUI tool still says 'media not detected', though.

All the files on the floppy belong to the 'root', not to the user, so we need to copy them onto a user directory for editing them.

I don't see the reason for this weird behavior regarding the small fstab entry. Could anyone teach?

Hello,
As for myself, I can't tell you the reason for that weird behavior, but since I had the same problem, I applied you idea, and I got the same result. So at least I can access my floppies by now :).

---

### Post by ron999 on 2010-04-15
Great!
Commenting out the /dev/fd0 entry in the /etc/fstab file has solved my problem too.:)

So now to mount my disks I can use:-
```
sudo mount /dev/fd0 /media/floppy0
```

Then use **sudo nautilus** to copy files from floppy to desktop.

Then unmount the disk using:-
```
sudo umount /dev/fd0

```

:) :P :)

---

### Post by HiSiskin on 2010-04-15
Could anyone explain what is happening around Ubuntu, floppy disk and /etc/fstab entry?
Why on earth did we need to delete/comment-out the entry from the fstab file before mounting the floppy disk? :confused:

---

### Post by Objekt on 2010-04-21
No solution here so far.  I simply can't access my 3.5" diskette drive, no matter what, under Ubuntu.

It works fine when I run Windows (either XP or 7).  

Given that I know the diskette is fine, and the drive works, I don't understand why I can't access it from within Ubuntu.

---

### Post by ron999 on 2010-04-21
Have you bothered to read this whole thread and not just the title?

---

### Post by HiSiskin on 2010-04-22
> **Objekt said:**
> No solution here so far.  I simply can't access my 3.5" diskette drive, no matter what, under Ubuntu.

It works fine when I run Windows (either XP or 7).  

Given that I know the diskette is fine, and the drive works, I don't understand why I can't access it from within Ubuntu.
Describe your situation detailedly, please.
1) 'Cat' the /etc/fstab
2) Do you have device fd0 on the /dev directory?
3) What method did you use mounting the floppy?
4) What sub-directories your /media dir has?
...etc., etc.

---

### Post by Objekt on 2010-04-22
> **HiSiskin said:**
> Describe your situation detailedly, please.
1) 'Cat' the /etc/fstab

```
objekt910@objekt910-desktop:~/bin/Brother$ sudo cat /etc/fstab
proc            /proc           proc    defaults        0       0
UUID=075bba33-2604-4962-8456-bc020ec81c33 /               ext3    errors=remount-ro 0       1
UUID=4e708513-c001-465a-84cb-3f8f24ffac39 /home           ext3    defaults        0       2
#UUID=a0d8d106-2e58-4c54-ac12-e05498e96c2d none            swap    #sw              0       0

#Attempt to fix booting problem 18 Apr 2010
#UUID=3fba81a3-de14-4f56-9e7b-ace95d933a0e none            swap    sw              0       0
UUID=6af0cef2-ebe2-45b5-8f09-f05b2d8802cd none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0

#experimental line
/dev/sda2 /media/Storage ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1

#another experimental line
/dev/sdd1 /media/OldWD ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1

#yet another for the new ext3 partition
#old reference: /dev/sdc3 

UUID=d6dbe37d-d487-474d-9e14-9db95cb10297	/media/UbuntuStorage ext3 defaults 0 2
```

> **HiSiskin said:**
> 2) Do you have device fd0 on the /dev directory?
Yes.
> **HiSiskin said:**
> 3) What method did you use mounting the floppy?
Tried it a couple of ways:

1) Clicked on the "floppy0" drive in the list of drives in Nautilus.  The drive makes noise and the light comes on, but nothing appears in Nautilus.

2) At the CLI:
```
objekt910@objekt910-desktop:/media/floppy$ sudo mount /dev/fd0
objekt910@objekt910-desktop:/media/floppy$ sudo mount /dev/fd0 /media/floppy -t vfat
```

Neither command does anything.  

> **HiSiskin said:**
> 4) What sub-directories your /media dir has?
...etc., etc.

```
objekt910@objekt910-desktop:/media$ ls
8D2B-93AF  cdrom  cdrom0  cdrom1  DiscImage  floppy  floppy0  OldWD  sdd1  Storage  UbuntuStorage
```

8D2B-93AF is a USB flash stick that I had mounted at the time.  DiscImage is an empty folder I keep around for mounting...well, disc images (*.iso's).  OldWD, sd1, Storage, and Ubuntu Storage represent various partitions, both NTFS and ext3.

Any ideas?  It sure looks like there should be something in the /floppy folder, but it's always empty.

Also, I don't see a "floppy" icon show up on the desktop.  I'm pretty sure that worked when I was running Kubuntu 8.04.

---

### Post by HiSiskin on 2010-04-25
Hi Object,

1) Comment out the /dev/fd0 line on your /etc/fstab file.
--- Also, delete all of your experimental lines.

2) Then do:
   sudo mount -t vfat /dev/fd0 /media/floppy0

--- If it is a dos floppy,
-t msdos
shoud be used.

---

### Post by HiSiskin on 2010-04-26
Also, this link might help:
[http://justanotherwebblog.wordpress.com/2009/03/01/howto-use-floppy-in-ubuntu-810/](http://justanotherwebblog.wordpress.com/2009/03/01/howto-use-floppy-in-ubuntu-810/)

---

### Post by Objekt on 2010-04-26
Thanks, that did the trick.

The link was especially helpful.

---

### Post by murphyac on 2010-07-13
> **HiSiskin said:**
> Hi Object,

1) Comment out the /dev/fd0 line on your /etc/fstab file.
--- Also, delete all of your experimental lines.

2) Then do:
   sudo mount -t vfat /dev/fd0 /media/floppy0

--- If it is a dos floppy,
-t msdos
shoud be used.

Thank you for this information.  Your method is the only way I can get my floppy drive and files seen and read.  Although clicking on "Floppy Drive" on the "Places" menu makes the drive light go on and starts the motor, the files are not read and displayed.  It's a bit more work to go through the terminal, to mount and unmount the drive (using sudo umount -t vfat /dev/f0 /media/floppy0), but at least I can see and transfer files.  My drive is a plain old motherboard-attached floppy on a Dell Dimension 4700.  I am using Lucid Lynx, with kernel 2.6.32-23-generic.
       Strangely enough, I remember being able to read and write to floppies previously, but something has obviously changed, I don't know when.
        Unfortunately, the procedure in the link you gave did not work for me, but, happily, your workaround did.
       One question, (sorry, I'm a bit of a newbie) am I correct in assuming that vfat is a standard floppy format and can be used for various operating systems?
       Thanks again.
Angela C. Murphy:)

---

### Post by plucky on 2010-07-13
> **murphyac said:**
> Thank you for this information.  Your method is the only way I can get my floppy drive and files seen and read.  Although clicking on "Floppy Drive" on the "Places" menu makes the drive light go on and starts the motor, the files are not read and displayed.  It's a bit more work to go through the terminal, to mount and unmount the drive (using sudo umount -t vfat /dev/f0 /media/floppy0), but at least I can see and transfer files.  My drive is a plain old motherboard-attached floppy on a Dell Dimension 4700.  I am using Lucid Lynx, with kernel 2.6.32-23-generic.
       Strangely enough, I remember being able to read and write to floppies previously, but something has obviously changed, I don't know when.
        Unfortunately, the procedure in the link you gave did not work for me, but, happily, your workaround did.
       One question, (sorry, I'm a bit of a newbie) am I correct in assuming that vfat is a standard floppy format and can be used for various operating systems?
       Thanks again.
Angela C. Murphy:)


[http://ubuntuforums.org/showpost.php?p=9527243&postcount=37](http://ubuntuforums.org/showpost.php?p=9527243&postcount=37)

This solution works in Lucid.

You also have to pin the package version as the update manager will try to change it back to the version that doesn't work.

Good Luck

---

### Post by murphyac on 2010-07-14
Thanks plucky.
I uncommented the floppy line in /etc/fstab, then went to Synaptic and followed the procedure in the link you gave, I then locked in the old udisks version. Floppy is working fine now.
How will I find out if Ubuntu fixes the bug in a future upgrade so it's safe to unlock udisks?
Angela C. Murphy:)

---

### Post by and003 on 2010-08-08
> **HiSiskin said:**
> Also, this link might help:
[http://justanotherwebblog.wordpress.com/2009/03/01/howto-use-floppy-in-ubuntu-810/](http://justanotherwebblog.wordpress.com/2009/03/01/howto-use-floppy-in-ubuntu-810/)
I tried this method and it seems to partially work for me. When I tried to access the floppy with Dolphin, the drive activated and searched, but it couldn't determine the file system on its own, even when I used the word 'auto' in the "sudo mount" command. 

I tried mounting my floppy after adding both MS-DOS of VFAT, but it still didn't work. What else do I need to do?

I am attaching documentation to this post in a ZIP file.

---

### Post by and003 on 2010-08-21
> **Objekt said:**
> No solution here so far.  I simply can't access my 3.5" diskette drive, no matter what, under Ubuntu.

It works fine when I run Windows (either XP or 7).  

Given that I know the diskette is fine, and the drive works, I don't understand why I can't access it from within Ubuntu.
You can mount and access your diskette drive with step-by-step information found here:
[https://answers.launchpad.net/ubuntu/+source/util-linux/+question/120571](https://answers.launchpad.net/ubuntu/+source/util-linux/+question/120571)

---

### Post by Objekt on 2010-08-23
Well, not really.  That thread is all about Ubuntu 10.04.  Synaptic shows no such packages as "udisks," as mentioned in the thread you linked.  Is that a 10.04 vs. 9.10 thing?

There is also no "Use floppies" under the list of things users can do in the "Users and Groups" applet.  Maybe this is another difference between Ubuntu 9.10 and 10.04?

For what it's worth, here are the contents of my /etc/modules file:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc

# Generated by sensors-detect on Sun Jan 17 15:08:26 2010
# Chip drivers
w83627ehf
coretemp
vhba

#Add 3.5" diskette support
floppy
```

That last bit is supposed to enable use of the 3.5" diskette drive, but it doesn't.  Actually I get no response at all from inserting a diskette.  The drive light doesn't even come on.

If I click on the "Floppy" item in the "Places" list of Nautilus, nothing happens.  If I go to "Places->Removable Media->Floppy Drive" from the main GNOME menu bar, I hear the drive do something, but the light doesn't come on and no window opens.

Perhaps my diskette drive no longer works?  I'll have to boot into Windows XP to check it out.

---

### Post by and003 on 2010-08-23
Objekt, I acquired a version of 'udisks' for 10.04, the version of Ubuntu that I use, but if you're using 9.10, then try this package:

Ubuntu Packages: fdutils
[http://packages.ubuntu.com/karmic/fdutils](http://packages.ubuntu.com/karmic/fdutils)

It should allow you to mount a floppy.

---

### Post by Objekt on 2010-08-24
I already have fdutils installed, along with all the dependencies.

Not quite "nothing" happens when I try to go to the floppy drive in Nautilus: the drive light does come on, as if the machine were trying to read the disk.  But I never get any indication that there's anything on the disk, not even a window showing it as blank (which it isn't - I confirmed under Windows XP that there are files on it and that it should be readable).

This is very frustrating.

---

### Post by jefelex on 2010-09-02
I have the exact same problem - use to work fine in 8.10 - now in 9.10, the light comes on for a second and goes out - media not found.  I'm trying some of the links posted, I'm just adding my 2cents

John

---

### Post by Objekt on 2010-09-02
No progress here either.  My desktop's power supply died early this week, so I can't even try anything regarding the 3.5" diskettes.  I'm stuck on a netbook until I get a new PS for the desktop.

---

### Post by Bert Mariën on 2010-09-12
Has anyone filed a bug at launchpad yet?

I also have the same problem, but downgrading udisks works for me.

---

### Post by Objekt on 2010-09-14
Just so we're clear, you are talking of Ubuntu 9.10, yes?  I don't have any such package as "udisks" or "udisk" listed in Synaptic.

---

### Post by Bert Mariën on 2010-09-15
Nu, I am talking Lucid (10.04)

---

### Post by Objekt on 2010-09-15
Doh.  I guess I need to start my own thread about 3.5" diskette use in Ubuntu 9.10.  I don't currently have 10.04 on my desktop.

---

### Post by AVH on 2010-09-21
I have had the same problem in 10.04. The solution at [http://justanotherwebblog.wordpress.com/2009/03/01/howto-use-floppy-in-ubuntu-810/](http://justanotherwebblog.wordpress.com/2009/03/01/howto-use-floppy-in-ubuntu-810/)  worked for me as long as I removed the line in fstab about the floppy drive. I could then mount and use the drive manually. The solution of reverting Udisks to ver. 1.0.1-1build1 [https://answers.launchpad.net/ubuntu/+source/util-linux/+question/120571](https://answers.launchpad.net/ubuntu/+source/util-linux/+question/120571)  allowed me to mount and use the floppy in Nautilus.

---

### Post by Objekt on 2010-09-22
Yay!  The procedure you suggest did fix floppy access in 10.04!

Yes, I installed 10.04 alongside 9.10.  Wanted to see what all the fuss was about.  Liking it so far.

FWIW, 9.10 doesn't have a "udisks" package.  Also the "users and groups" applet is different; floppy access isn't a listed privilege that you can turn on and off.  Still have no idea how to enable floppy access under Karmic.

---

### Post by acrichardt on 2010-09-23
Hello all!  I have been having the same problem, but none of the fixes suggested have helped my case at all.  What is particularly confusing about my situation is that the first time I installed (Lubuntu 10.4) I had absolutely no problem mounting fd0.  In fact, just typing 

$ sudo mount /dev/fd0

and 

$ sudo mount /dev/fd1 (I have two drives)

worked just fine.  Well, making a rookie mistake I deleted an important, unrelated directory as root while trying to customize and had to do a re-install.  After the fresh install i can no longer mount my floppy drives.  My time card at work is stored on it (I could run to a Windows machine in the building and copy to USB, but that is an absurd notion [-( .Can anyone help?  Here are some commented clips of my process.

 $ ls /dev | grep fd*
ecryptfs
fb0
fd
fd0
fd0u1040
fd0u1120
... (list continues a bit)

# /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# /dev/fd1        /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0
(commented out, then after reboot I get the next message)

$ sudo mount /dev/fd0
mount: can't find /dev/fd0 in /etc/fstab or /etc/mtab
(so I uncommented, and rebooted.  The next series is the common problem I have)

$ ls /media
floppy  floppy0  floppy1

$ sudo mount /dev/fd0 /media/floppy0  <------disk not inserted
mount: /dev/fd0 is not a valid block device

$ sudo mount /dev/fd0 /media/floppy0  <------disk inserted.  I can hear the drive trying to access and drive LED is on.

$ ls /media/floppy0

$ sudo umount /dev/fd0
umount: /dev/fd0: not mounted

The drive tries to access, it is not writ-protected, but alas no mounted filesystem.  The same effect if I specify -t vfat or -a with mount command.

I'm trying to diagnose the problem since it functioned once before with no effort or installation of other programs, unless I'm overlooking something major.

I'm stumped.

Thank you.

P.S.  I did add floppy to /etc/modules to load at boot.  I can't remember if I had fd0 & fd1 commented out of fstab at that stage or not.  Would that make a difference?  Thanks again!

---

### Post by acrichardt on 2010-09-23
hmm. I thought I fixed it.  The floppy drives were there, then when I upgraded and updated, then autoremove to clean the system, they disappear.  interesting.:-k

---

### Post by grahammechanical on 2010-09-23
This may be irrelevant but Use Floppy Drives is a user privilege. If you are set as administrator you may have this privilege but if you have been set to Custom (as I some how happened to be) then you may not have the privilege of using a floppy drive.

regards

---

### Post by acrichardt on 2010-09-24
Well, I thank you for the suggestion.  My account did not have floppy access enabled, however after third install i was still able to mount from the command line anyway.  I still turned them on.  Then I did another update && upgrade && autoremove && clean type combo and they were gone instantly after.  No access.  I checked and my account still had floppy access enabled.  Once again the drive works but does not show up.  Everything indicates it is there, but it isn't.  The drive works when I try to mount, but no icons and blank directory in folder manager.  This is a curious behavior that will need some super linux sleuthing.  Thank you though.  

P.S. also same process after su root / sudo bash same lack of floppy.:?:

---

### Post by Objekt on 2010-09-24
> **acrichardt said:**
> Well, I thank you for the suggestion.  My account did not have floppy access enabled, however after third install i was still able to mount from the command line anyway.  I still turned them on.  Then I did another update && upgrade && autoremove && clean type combo and they were gone instantly after.  No access.  I checked and my account still had floppy access enabled.  Once again the drive works but does not show up.  Everything indicates it is there, but it isn't.  The drive works when I try to mount, but no icons and blank directory in folder manager.  This is a curious behavior that will need some super linux sleuthing.  Thank you though.  

P.S. also same process after su root / sudo bash same lack of floppy.:?:

You know you need to roll back the "udisks" package to a previous version, yes?  Version 1.0.1-1build1 of udisks works; the current "update" version breaks floppy drive use.  You didn't mention it, so I wasn't sure whether you tried that.  For me, it was key to getting floppy access in my fresh Ubuntu 10.04 install (which is now at the 10.04.1 standard except for udisks).

---

### Post by AVH on 2010-09-24
> **acrichardt said:**
> Well, I thank you for the suggestion.  My account did not have floppy access enabled, however after third install i was still able to mount from the command line anyway.  I still turned them on.  Then I did another update && upgrade && autoremove && clean type combo and they were gone instantly after.

Have you also locked the reversion to prevent it from being updated?

---

### Post by acrichardt on 2010-09-30
YES!  Thank you guys!  That was the key.  I remember reading about the udisk downgrade, but I used the command line to remove and re-install the first time with unsatisfactory results.  Not sure what happened or what I did then (I try to use the command line as much as possible to learn more).  Using synaptic I downgraded and locked.  Now it works.  And I learned some new things I didn't know about synaptic.  Thank you very much!! \\:D/

---

### Post by TerrieG on 2010-10-05
I hadn't mounted my floppy for a while and experienced the same problems as others.  Your method works for me.  This is the second time in a year that I have encountered problems mounting my floppy because of updates I have installed.  GRRR.  Thanks for your posting

---

