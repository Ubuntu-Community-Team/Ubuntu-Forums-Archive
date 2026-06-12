---
title: "Ubuntu Hardy Heron boot failure"
date: 2010-05-19
forum: General Help
---

### Post by geminizin on 2010-05-19
I've been using Ubuntu Hardy Heron for over 1.5 years and there has been no major issue. Today booting failed. It got to the logo screen and then it's giving out a bunch of information on the screen, things like:

libselinux.so.i cannot open shared object file
status DRDY ERR
exception EMASK
write protect is off
error UNC

At the end it'd try to run in maintenance shell but said it couldn't. So it reboots after 5 seconds and this just loops forever.

I have Windows Vista installed on the laptop (dual-boot) and I could log into Windows successfully so I suppose this is not a hardware failure?

So there are 2 main things that I care:
1. How do I backup my data in Ubuntu?
2. How do I fix this?

Many thanks for the help.

---

### Post by ryan858 on 2010-05-19
Well, you can download a Live CD to do whatever you need, and backup or fix Ubuntu. You can download and burn it on Windows, then boot to it and do what you need.

It's available on the main Ubuntu website.

---

### Post by geminizin on 2010-05-19
> **ryan858 said:**
> Well, you can download a Live CD to do whatever you need, and backup or fix Ubuntu. You can download and burn it on Windows, then boot to it and do what you need.

It's available on the main Ubuntu website.

So you reckon my data is retrievable? That's a relief.

How do I go about fixing it?

Many thanks.

---

### Post by ryan858 on 2010-05-19
I don't know what any of those errors mean... Either way, I would need more information to know what's going on. Did you do anything out of the ordinary before this happened? Install or remove anything? Etc...

As far as whether your data is recoverable, it depends on what's going on, and what happened to cause it not to boot right. You'll pretty much have to see for yourself once you boot to the live cd... You can mount the hard disk (might happen automatically even) and check it out. You can use *chroot* to some extent to do stuff from within the installation itself, rather than from inside the live cd's OS.

First thing I would do if i were you, is download and burn the ISO, then boot to it, mount the Ubuntu partition, and backup all your data.

If you installed Hardy from a CD then you already have a Live CD, unless something happened to it, in which case you can download the Lucid CD, and maybe even upgrade while you're at it.

---

### Post by geminizin on 2010-05-19
> **ryan858 said:**
> I don't know what any of those errors mean... Either way, I would need more information to know what's going on. Did you do anything out of the ordinary before this happened? Install or remove anything? Etc...

As far as whether your data is recoverable, it depends on what's going on, and what happened to cause it not to boot right. You'll pretty much have to see for yourself once you boot to the live cd... You can mount the hard disk (might happen automatically even) and check it out. You can use *chroot* to some extent to do stuff from within the installation itself, rather than from inside the live cd's OS.

All I've done today before the boot failure was to sign out of Ubuntu and use IE7 in my Windows Vista to do some testing. I then rebooted the machine to try to go back to Ubuntu and the world collapsed.

---

### Post by zaphod777 on 2010-05-19
yes you should be able to copy all of your data off to a USB drive. I am not sure what that error is but you might wan't to run a disk check maybe there is an issue with the file system. IF everything works fine on the Live CD then it might be a good opportunity to upgrade to 10.04. 

You can run this from the Command line in the Live CD make sure you backup your data first just in case. 

Also if you get a warning that the file system is mounted make sure you unmount it using gparted first. 
```
fsck /dev/sda1
```

---

### Post by ryan858 on 2010-05-19
> **zaphod777 said:**
> Also if you get a warning that the file system is mounted make sure you unmount it using gparted first. 

I'm just curious, but why use gparted to unmount it? ***umount /dev/sda1*** is much easier.

---

### Post by zaphod777 on 2010-05-19
no reason I just didn't remember how to do it from the CL of the top of my head ;-)

---

### Post by geminizin on 2010-05-19
> **zaphod777 said:**
> yes you should be able to copy all of your data off to a USB drive. I am not sure what that error is but you might wan't to run a disk check maybe there is an issue with the file system. IF everything works fine on the Live CD then it might be a good opportunity to upgrade to 10.04. 

You can run this from the Command line in the Live CD make sure you backup your data first just in case. 

Also if you get a warning that the file system is mounted make sure you unmount it using gparted first. 
```
fsck /dev/sda1
```

LiveCD: Is that the original CD which I installed Ubuntu from?

---

### Post by amite on 2010-05-19
this question has asked severall times in this forum ........i think [http://ubuntuforums.org/showthread.php?t=937872](http://ubuntuforums.org/showthread.php?t=937872)  would help u....more

---

### Post by zaphod777 on 2010-05-19
> **geminizin said:**
> LiveCD: Is that the original CD which I installed Ubuntu from?

yes.

---

### Post by ryan858 on 2010-05-19
> **geminizin said:**
> LiveCD: Is that the original CD which I installed Ubuntu from?
Check out this article, it should explain everything you need to know about Live CD's:
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

### Post by geminizin on 2010-05-19
I have managed to fsck /dev/sda5 and /dev/sda6 using the installation CD. Now Ubuntu freezes during the boot. It just sits there without going to all those commands. If I boot it using the recover mode then it freezes at this:
Kernel pnic - not syncing: Attempted to kill init!

Any idea?

---

### Post by geminizin on 2010-05-19
I have managed to fsck my sda5 and sda6 and now I have a different  problem.

Ubuntu freezes at the logo screen, normally the orange progress bar goes  back and forth for a while and should start loading. Now it stucks  somewhere and just freezes. If I try to use the recovery mode, then I  get the following error and it freezes too:

Being: Running /scripts/init-bottom
no-init: /sbin/init: No such file or directory
Kernel panic - not syncing: Attempted to kill init!

It seems to me that Ubuntu somehow has lost the correct boot  configuration. How do I go about fixing this problem?

---

### Post by geminizin on 2010-05-19
Following up from this thread:
[http://ubuntuforums.org/showthread.php?t=1487453&page=1](http://ubuntuforums.org/showthread.php?t=1487453&page=1)
I have managed to fsck my sda5 and sda6 and now I have a different problem.

Ubuntu freezes at the logo screen, normally the orange progress bar goes back and forth for a while and should start loading. Now it stucks somewhere and just freezes. If I try to use the recovery mode, then I get the following error and it freezes too:

Being: Running /scripts/init-bottom
no-init: /sbin/init: No such file or directory
Kernel panic - not syncing: Attempted to kill init!

It seems to me that Ubuntu somehow has lost the correct boot configuration. How do I go about fixing this problem?

---

### Post by geminizin on 2010-05-19
By having the boot in verbose (non-quiet mode) I get to see more information:

Mounting root file system: didn't return ok.

How do I fix this?

---

### Post by geminizin on 2010-05-19
What's wrong with my fstab here?

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=b809a8dd-ee5c-424b-89e8-1434bb3d543b / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=37456e7e-b3c4-4d3b-aa28-f0ca9178531c /home ext3 relatime 0 2
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda2 /media/C ntfs umask=222,utf8 0 0

I'm on Ubuntu 8.0.4 Hardy Heron. I can't boot. It just freezes at the logo screen.

---

### Post by geminizin on 2010-05-19
Any idea?

---

### Post by geminizin on 2010-05-19
Somebody help me please.

---

### Post by geminizin on 2010-05-19
My Ubuntu is currently not bootable because of this:
[http://ubuntuforums.org/showthread.php?t=1487659](http://ubuntuforums.org/showthread.php?t=1487659)

I have a lot of settings and configurations for server, IDE etc. If I can backup the entire directory under root and copy it back after the re-installation, would I need to install all these softwares and configure them again?

Thanks for the help.

---

### Post by Copperline on 2010-05-19
Hi

Having read through this and the thread you mention at the start, I would say that it looks as though you still have major errors in your Ubuntu file system. The kernel errors in particular do not look good. This is either due to a failure of the hard drive itself (you could check this using badblocks: [http://manpages.ubuntu.com/manpages/jaunty/man8/badblocks.8.html](http://manpages.ubuntu.com/manpages/jaunty/man8/badblocks.8.html)) or the fsck process did not completely repair the file system.

Assuming that your HDD is not the problem then the problem will of course be within the file system. In my experience, the fsck process has not worked well and when it has...it has taken *hours*. If it is possible to recover your data from the file system on the drive, if I were in this situation myself, I would fresh-install. I know this seems drastic but having run fsck processes and still run into problems, you could spend far more time trying to fix the problems than it would take to re-install the fresh system and port things across. This is because I think your chances of finding what the problem is...if it is indeed just one file that is affected (which is extremely unlikely)...are very remote.

I hope this helps...if fresh-installing isn't an option then a rethink is needed :)

Cheers

---

### Post by cariboo on 2010-05-19
Please don't create multiple threads on the same subject, I have merged your three threads.

---

### Post by geminizin on 2010-05-19
> **Copperline said:**
> Hi

Having read through this and the thread you mention at the start, I would say that it looks as though you still have major errors in your Ubuntu file system. The kernel errors in particular do not look good. This is either due to a failure of the hard drive itself (you could check this using badblocks: [http://manpages.ubuntu.com/manpages/jaunty/man8/badblocks.8.html](http://manpages.ubuntu.com/manpages/jaunty/man8/badblocks.8.html)) or the fsck process did not completely repair the file system.

Assuming that your HDD is not the problem then the problem will of course be within the file system. In my experience, the fsck process has not worked well and when it has...it has taken *hours*. If it is possible to recover your data from the file system on the drive, if I were in this situation myself, I would fresh-install. I know this seems drastic but having run fsck processes and still run into problems, you could spend far more time trying to fix the problems than it would take to re-install the fresh system and port things across. This is because I think your chances of finding what the problem is...if it is indeed just one file that is affected (which is extremely unlikely)...are very remote.

I hope this helps...if fresh-installing isn't an option then a rethink is needed :)

Cheers

Thanks. Looks like maybe a re-installation is the best solution. If I backup everything under the root directory and copy it back after the installation do I get to avoid all the setups and configurations of my softwares such as server, IDE etc?

Thanks for the help.

---

### Post by geminizin on 2010-05-19
> **cariboo907 said:**
> Please don't create multiple threads on the same subject, I have merged your three threads.

Thanks. Sorry about that.

---

### Post by koolblue3 on 2010-05-19
> **geminizin said:**
> Thanks. Looks like maybe a re-installation is the best solution. If I backup everything under the root directory and copy it back after the installation do I get to avoid all the setups and configurations of my softwares such as server, IDE etc?

Thanks for the help.

Hi,

Things look quite hosed at this point. I also would recommend a fresh install. If you backed up your config files I don't see why they would not work if you copied them over to the new install. The only thing that may keep them from working is if the software has been updated and it now has a different config file layout and how it reads them. Are you just going to continue using 8.04 or are you going to upgrade to 10.04?

---

### Post by Copperline on 2010-05-19
> **geminizin said:**
> Thanks. Looks like maybe a re-installation is the best solution. If I backup everything under the root directory and copy it back after the installation do I get to avoid all the setups and configurations of my softwares such as server, IDE etc?

Thanks for the help.


Yes...backing up all of your /home directory (as long as you don't forget the hidden files too as these are REALLY important for this to work!) will preserve your settings. When I did this I found this website really helpful:

[http://linuxologist.com/linuxhowto/howto-fresh-ubuntu-install-without-losing-your-current-settings/](http://linuxologist.com/linuxhowto/howto-fresh-ubuntu-install-without-losing-your-current-settings/)

---

### Post by geminizin on 2010-05-19
> **koolblue3 said:**
> Hi,

Things look quite hosed at this point. I also would recommend a fresh install. If you backed up your config files I don't see why they would not work if you copied them over to the new install. The only thing that may keep them from working is if the software has been updated and it now has a different config file layout and how it reads them. Are you just going to continue using 8.04 or are you going to upgrade to 10.04?

I think I'll keep going with 8.04 as there might be a lot of new and different things in 10.04 and I don't really enjoy configuring :)

---

### Post by geminizin on 2010-05-19
> **Copperline said:**
> Yes...backing up all of your /home directory (as long as you don't forget the hidden files too as these are REALLY important for this to work!) will preserve your settings. When I did this I found this website really helpful:

[http://linuxologist.com/linuxhowto/howto-fresh-ubuntu-install-without-losing-your-current-settings/](http://linuxologist.com/linuxhowto/howto-fresh-ubuntu-install-without-losing-your-current-settings/)

Perhaps also stuff under root directory? I have Tomcat and Apache outside of home.

---

### Post by Copperline on 2010-05-19
Oops...I'm sorry forgot to mention...if keeping your configuration settings don't change to a different version or you'll mess things up! Stick with 8.04 and if you want to progress to other versions then you can upgrade. The config settings won't work across releases and of course they must be used on the same system as they came from.

Copperline

---

### Post by Copperline on 2010-05-19
I don't think you need your /root as the file system considers /home to be the root partition for all of your settings but you could just to be sure.
I have only ever heard of backing up /home in this circumstance.

There are some excellent instructions here:

[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

about how to back up /home effectively using rsync rather than copy and paste in file manager. Apparently rsync is better as the copy and paste way can invoke errors.

By the way...if the command line isn't helpful to you then install  *grsync* which is very good and is the graphical front-end for *rsync *and I find it is more intuitive[I] (sudo apt-get install grsync).
[/I]

---

### Post by ryan858 on 2010-05-19
Am I correct to think that he can do a fresh install of 8.04 and then transfer the settings, then upgrade via Update Manager to 10.04 without losing all his settings?

---

### Post by Copperline on 2010-05-19
You are correct indeed...configuration settings can be preserved for a fresh install (if, of course they are backed up first before the fresh install and in the correct way...see my previous post and use grsync for this as it will make sure you capture everything) and you can directly upgrade to Ubuntu 10.04 LTS from both Ubuntu 9.10 and from Ubuntu 8.04. If you have other versions you must read the Upgrade Notes here: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes) in order to carry out the upgrade.

---

### Post by ryan858 on 2010-05-19
Hmm, I recall having to do an incremental upgrade from 9.04 to 9.10, and finally to 10.04, using Update Manager... But it also broke my installation... And I haven't a clue why. I didn't bother to figure it out since it was a new install of 9.04 anyway. I just reformatted the drive and installed 10.04 directly from a CD.

Another anomaly that I noticed while downloading 10.04, is that it was described as an unstable beta as well as an LTS... Isn't this contradictory?

edit: I can't seem to find the contradiction anymore, maybe it was just an error by the webmasters... Website also says that you can only upgrade from 8.04 LTS or 9.10. I figure that's why 9.04 had to upgrade incrementally. Still no clue why 9.10 to 10.04 broke it...

Sorry, I realize this is getting irrelevant to the topic fast... I'll stop now.

---

### Post by Copperline on 2010-05-20
Goodness knows why that broke your system but I've had the same sort of issue previously and now I always fresh-install as I think the upgrade business spoils things.

I haven't heard of it being described as an unstable beta myself (although I'm quite prepared to believe it as it's caused me quite a few problems) but I would think it was contradictory as well. LTS releases are supposed to be stable after all.

---

### Post by geminizin on 2010-05-22
I was trying to re-install Ubuntu 8.04.1 also known as Hardy Heron.  There were 2 problems I had:

1. The installation got to 53% and gave out an error saying "The  installer encountered an error copying files to the hard disk, Errno 5  input/ouput error". I googled on this and it seems that it's either a  CD-ROM or hard disk problem. I tried it with an external CD drive and  same thing happened so I guess the problem is with my hard drive? If  that's the case, is it possible to install Ubuntu to a portion of hard drive and hopefully it's the part that doesn't have any hardware failure?

2. When I was at the partition stage, there were 3 options: guided, guided with the whole disk and manual. I think I used one of the first 2 and it erased my Windows installation. Now my whole drive is a big 250GB partition. Since my installation failed anyway, is it possible to revert this and get my Windows installation back? If not, how do I retrieve data under Windows?

Many thanks for the help.

---

### Post by Copperline on 2010-05-22
> **geminizin said:**
> I was trying to re-install Ubuntu 8.04.1 also known as Hardy Heron.  There were 2 problems I had:

1. The installation got to 53% and gave out an error saying "The  installer encountered an error copying files to the hard disk, Errno 5  input/ouput error". I googled on this and it seems that it's either a  CD-ROM or hard disk problem. I tried it with an external CD drive and  same thing happened so I guess the problem is with my hard drive? If  that's the case, is it possible to install Ubuntu to a portion of hard drive and hopefully it's the part that doesn't have any hardware failure?

2. When I was at the partition stage, there were 3 options: guided, guided with the whole disk and manual. I think I used one of the first 2 and it erased my Windows installation. Now my whole drive is a big 250GB partition. Since my installation failed anyway, is it possible to revert this and get my Windows installation back? If not, how do I retrieve data under Windows?

Many thanks for the help.

Not a problem :)

1. An input/output error or I/O Error as it will sometimes appear is due to the CD-ROM...but not necessarily the drive. The problem could be with the CD...and it doesn't necessarily mean it's scratched. When CD's are written, errors are actually quite common but the technology works in such a way as for the drive to be able to work around the error. This may not be happening here or the I/O error may be too much for the drive to work out. Whatever the reason I would check the CD first just to be sure...there's an option to do this on the LiveCD boot screen. Technically it checks the checksum...so if this comes back as being ok then you know your disc is sound. It would help to run the disc check on the disc in same drive as you burnt it. I don't think that error is due to the hard drive...but you could try moving the partition if you like and seeing if that makes a difference. (I think the disc issue is more likely though to be honest. Sometimes people have to do silly things such as burn several discs in order to find one that works. I have no idea why...but it can only be due to the error writing and correction business that goes on behind the scenes of writing CDROMs). It is also a good point to mention that burning the disc on the slowest possible speed is a good idea (K3b will burn at 1x and NERO also has this feature). It will take a while but greatly reduces the chance of errors. If you were feeling brave and have several hours to spare you could check your hard drive for bad blocks using badblocks...but I do doubt that it will be worth the (considerably long, usually) wait.

2. Oh dear...that is quite disastrous I'm afraid. It isn't possible to revert the partitioning process once it's happened. Software does exist under Windows to retrieve data...even when a drive has been re-partitioned but it is expensive and it doesn't always work. EASEUS Data Rescue is one I'm familiar with but...it does have the cost issue.

Under Ubuntu/Linux, there are a few options...testdisk and photorec are the most well-known (confusingly, you need to install testdisk to get photorec) and they are good...but they can take **hours**, must be run from a LiveCD in which the partition is NOT mounted, are fairly tricky to use (although there are helpful web pages to show you how) and may not yield results that are actually any use to you. If the drive has simply been re-partitioned then you do stand a chance of recovering your data but if that data has subsequently been over-written (which some of it probably has)...with a different filesystem to which the whole partition has also been re-formatted (8.04 uses ext3 file system and Windows is likely NTFS) then I imagine you'd need the security services. I don't mean to sound flippant here but it sounds like you'll be into a major recovery operation that standard software won't be able to work out due to the differences in file systems involved and the fact that once over-written, recovery of data from a hard-drive by the home user is unlikely. However, I'd give photorec a try if you're feeling game...or you may be lucky and somebody with a greater knowledge of advanced file recovery may be able to help you on here.

I hope this helps and I am sorry about your partition issue...I've done the same myself so I'm afraid I write with experience on this one! :)

Copperline

---

### Post by geminizin on 2010-05-25
I have successfully re-installed Ubuntu but now I've got a problem trying to import my stuff back. I have backed up everything under my home directory. When I try to change the user's home directory to be the one I've backed up, I get an error at the login screen and therefore I'm unable to log in. The error says:

User's $HOME/.dmrc file is being ignored...etc

What's going on here?

---

### Post by Copperline on 2010-05-26
> **geminizin said:**
> I have successfully re-installed Ubuntu but now I've got a problem trying to import my stuff back. I have backed up everything under my home directory. When I try to change the user's home directory to be the one I've backed up, I get an error at the login screen and therefore I'm unable to log in. The error says:

User's $HOME/.dmrc file is being ignored...etc

What's going on here?

Hi I'm sorry this is a bit late! I haven't been able to get in front of my computer for a short time! This link looks helpful:

 [http://ubuntuforums.org/archive/index.php/t-491591.html](http://ubuntuforums.org/archive/index.php/t-491591.html)

it's easier for you to look at it there rather than me typing it all out because you can follow the problem through and it will make more sense. I'm sure reading through it (you may need to scroll right down to the bottom he person posting seems to have found a fix) will solve your issue. However...if it doesn't please post back!

Cheers
Copperline

---

