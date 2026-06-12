---
title: "removing windows from dual boot"
date: 2012-07-10
forum: General Help
---

### Post by johnplov on 2012-07-10
I've got an old computer that came with windows ME, and when I bought a replacement a few years ago, I put Ubuntu Hardy Heron on the old one as a dual boot. I want to update to the latest distro, but the hard drive hasn't got room. I don't use the old windows anyway, so I'd happily take it off if it won't cause me problems with the existing Ubuntu.  Is there a quick way to get rid of it? can I just delete the partition? I don't want to start over from scratch if I can avoid it.
Thanks for your help

---

### Post by zwygart on 2012-07-10
Yes, you can just delete the partition. 

The only case in wich this will cause problems is when the bootloader of Windows is used or if the boot process goes trough this partition. But this situation occurs rarely and only if someone installed Linux in a strange way. 

In your place I would just delete the partition and if problems occur, the forum is here to help.

---

### Post by josue0098 on 2012-07-10
Get a ubuntu live cd, boot it up, install G-parted. Then, delete the windows partition and expand the ubuntu partition to take the whole disc. :)

---

### Post by mkstallings1 on 2012-07-10
I agree.  Use gparted.  Just make sure you backup before you do anything.

---

### Post by johnplov on 2012-07-10
Thanks, I'll give that a shot.

---

### Post by Easy Limits on 2012-07-10
You can always just download gparted, burn to a cd, then boot from it.

---

### Post by johnplov on 2012-07-11
I'm having trouble figuring out how to use gparted.  I have three partitions; one with windows, one with my wife's account, and one with my account.  I successfully shrank the windows partition to create some room, and I can expand the partition with my wife's account, but it won't let me expand my partition.  I'm guessing that is because it is the active partition, but I don't know how to get around that. I tried signing into my wife's account to try from there, but I can't get it to accept my administrator password.
If i could just expand my partition, I can do the upgrade to 10.04 pretty painlessly, but it gets partway through and then says there isn't enough space.
Any suggestions would be greatly appreciated

---

### Post by Ubun2to on 2012-07-11
> **johnplov said:**
> I'm having trouble figuring out how to use gparted.  I have three partitions; one with windows, one with my wife's account, and one with my account.  I successfully shrank the windows partition to create some room, and I can expand the partition with my wife's account, but it won't let me expand my partition.  I'm guessing that is because it is the active partition, but I don't know how to get around that. I tried signing into my wife's account to try from there, but I can't get it to accept my administrator password.
If i could just expand my partition, I can do the upgrade to 10.04 pretty painlessly, but it gets partway through and then says there isn't enough space.
Any suggestions would be greatly appreciated

You should use a live CD to do this-then you aren't using the hard drive for anything.
Right click on the Windows partition and delete it. Then, expand your partition.

---

### Post by zwygart on 2012-07-12
I'm just surprised that you can modify partition on a disk that you booted on. Even if you booted on another partition, usually you just can't modify the partition table of that disk. Or am I wrong. 

So there are different scenarios : You have multiple disks, one with Windows and your wifes account and the other with Linux and your account.And your wifes account will mount in some unusual (not impossible) way. I don't think this is your case. 

When you modified the partitions, how did you connect to the computer? Trough your account or a LiveCD?

Another possibility is that Windows and your wifes account are on primary partition and yours and Linux on extended. Do you know the difference? In this case if you want remove(shrink) windows and extend and Linux, you should first extend the extended partition wich is one level Higher than the partitions it contains. You will see it Labeled extend. Once done you can extend the partitions in the extended partitions. 

To see how your computer is arranged post the out put of : sudo fdisk -l. 

If you want to use gparted from your wifes account try following in a terminal : sudo gparted. May be this won't work and explains why you can't start gparted from here account : she's not in the sudoers list.

---

### Post by johnplov on 2012-07-12
I've downloaded 10.10 and 12.04,and burned cds.  both will boot on my primary computer.  When I try to boot them on the older computer, it looks like it is going to boot, but stops and I get :
BusyBox v1.15.3 (ubuntu 1:1.5.3-ubuntu 5) built in shell (ash)
Enter 'help' for a list of built in-commands
(initramfs) unable to find a medium containing a live file system.

I was going to follow advice and run gparted off the live disk, but I can't seem to get beyond this point. Why would it load on one computer but not the other? I also have an older version, 7.04 factory disk that was used for the initial installation, I'll try that to see if it will load, aand if it has gparted maybe I can get it to work that way.
Thanks

---

### Post by oldfred on 2012-07-12
If computer is that old, how much RAM does it have? You may need Lubuntu or one of the more lightweight versions as the new gui require a lot of RAM.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

I also assume you are using the 32 bit version.

---

### Post by johnplov on 2012-07-12
I've only got 256 meg of ram,so maybe that is the problem.  It worked fine with hardy heron, but maybe that's not good enough for the new distros. I'll try one of the smaller ones
Thanks

---

### Post by zwygart on 2012-07-12
If you are willing to learn, make new experiences and have some time, you may also try others light distros like Puppy Linux wich is a very leight weight Linux (91 Mo) and runs only in ram. I also successfully installed ArchLinux on a computer with 256 Ram, Dell of the year 200. 20G Disk and a processor of 800MHz. Today my brother use it and enjoy to do school work and listen music. Video are tough but it's still usable. Just no gaming. :)

---

### Post by johnplov on 2012-07-12
I've got Lubuntu downloaded and burnt, and I'm now trying it in the old computer to see if it will load. I've tried Puppy in the past, but I never got the email to work.  Other than that, it looked okay for what we use the old computer for.  I am intrigued by the idea of just downloading gparted by itself and booting it, think maybe I'll try that.  Lubuntu didn't seem to have it, but maybe I just haven't looked hard enough.

---

### Post by johnplov on 2012-07-14
I've now tried loading a cd with gparted, and also cds with several different ubuntu editions, and I keep getting the busybox result.
Yesterday I tried puppy linux, and get as far as:

 searching for puppy files in computer disk drives
searching deeper, sub-sub folders in partitions...l=Lupu-528.sfs not found
dropping out -0 initial- ram disk console...
/bin/sh: can't access tty; job control turned off

All of the Ubuntu cds, the gparted, and the Puppy load fine onmy other computer. Could there be a hardware problem causing this?  The currently installed Ubuntu works,but I can't update it without creating more room.
Thanks for any help you can give me.:confused:

---

### Post by oldfred on 2012-07-14
If CDs work on anther computer that eliminates the possibility of bad CD.

If system boots and runs system seems ok, so is CD drive itself ok?  Sometimes just cleaning the lens on the CD may help. Not particularly easy to get to.

How to clean CD lens:
[http://members.iinet.net.au/~herman546/p27.html](http://members.iinet.net.au/~herman546/p27.html)

---

### Post by zwygart on 2012-07-16
Just a little question about your try with Puppy : did you wait enough time? 

This message may not mean that the boot process will not achieve. I several times recieve a similar message, but then I just waited and the boot process continued. On slow/old computers this time may be longer. Just wait several minutes and may be it will go trough.

---

### Post by johnplov on 2012-07-22
I finally managed to get gparted onto the old machine.  None of the ubuntu distros would load, and gparted by itself wouldn't load.  I tried Puppylinux 5.2.8, which I like, but it wouldn't load on the old machine either.  Finally I got puppy linux2.15 and it loads fine. Gparted shows the drive as:
 /dev/hda 18.65 GiB
with the partitons:
 /dev/hda1 Fat32 6.00 Gib total, 2.92  used,3.07 unused,  boot, lba

/dev/hda3 ext3 7.39 GiB, 6.89 used, 511.09 MiB unused

/dev/hda2 extended 4.16 Gib   lba

---

### Post by johnplov on 2012-07-22
I finally managed to get gparted onto the old machine.  None of the ubuntu distros would load, and gparted by itself wouldn't load.  I tried Puppylinux 5.2.8, which I like, but it wouldn't load on the old machine either.  Finally I got puppy linux2.15 and it loads fine. Gparted shows the drive as:
 /dev/hda 18.65 GiB
with the partitons:
 /dev/hda1 Fat32 6.00 Gib total, 2.92  used,3.07 unused,  boot, lba

/dev/hda3 ext3 7.39 GiB, 6.89 used, 511.09 MiB unused

/dev/hda2 extended 4.16 Gib   lba

/dev/hda5 fat32  3.77 Gib, 2.20 used, 1.57 unused

Now, I realized I'm not quite sure which partition has the windows ME on it, and I don't want to make a mistake and delete the wrong one. I'm guessing the two partitions with fat 32 are windows C: and D: Is that right.   The worst that could happen is that I delete Ubuntu, but give that I've had so much trouble getting a cd to boot, I don't want to make that mistake,  so I'm asking for advice first.
Thanks for your help.  This has been a lot harder than it would probably need to be, if I wasn't fumbling in the dark.

---

### Post by johnplov on 2012-07-22
I've attached a screenshot of gparted, should have done it before, but I had trouble figuring out how do do it from one computer to another.

---

### Post by oldfred on 2012-07-22
Cannot make out screen shot.

With Windows the boot flag is the active partition or the one the system boots from. Up until Windows 7 that was always the system partition also. Windows 7 often uses a separate boot partition that has the boot flag.

So I am pretty sure your install is in hda1 or the first partition.

---

### Post by Ubun2to on 2012-07-24
> **johnplov said:**
> I finally managed to get gparted onto the old machine.  None of the ubuntu distros would load, and gparted by itself wouldn't load.  I tried Puppylinux 5.2.8, which I like, but it wouldn't load on the old machine either.  Finally I got puppy linux2.15 and it loads fine. Gparted shows the drive as:
 /dev/hda 18.65 GiB
with the partitons:
 /dev/hda1 Fat32 6.00 Gib total, 2.92  used,3.07 unused,  boot, lba

/dev/hda3 ext3 7.39 GiB, 6.89 used, 511.09 MiB unused

/dev/hda2 extended 4.16 Gib   lba

/dev/hda5 fat32  3.77 Gib, 2.20 used, 1.57 unused

Now, I realized I'm not quite sure which partition has the windows ME on it, and I don't want to make a mistake and delete the wrong one. I'm guessing the two partitions with fat 32 are windows C: and D: Is that right.   The worst that could happen is that I delete Ubuntu, but give that I've had so much trouble getting a cd to boot, I don't want to make that mistake,  so I'm asking for advice first.
Thanks for your help.  This has been a lot harder than it would probably need to be, if I wasn't fumbling in the dark.

Well, Linux distros use either ext2, ext3, or ext4 usually. I have no idea what data the other partitions would have.
Windows uses the Fat32 and NTFS filesystems-I think it is safe to delete the Fat32 partitions.
I have a feeling the extended partition could be swap space, although, because of the size of the partition compared to your memory, I think it might not be. Swap space on older machines can usually be calculated as 2x the amount of memory. This is 4.16 GB. So, the swap space should be 0.5 GB, unless you were paranoid about running out of swap space, although 1 GB should be enough for even an extremely paranoid person. So, I'm not sure about the extended partition right now, since there are no used/free space stats available.

---

### Post by johnplov on 2012-07-24
i left a partition off of the list: /dev/sda6 linux swap 392.15 MiB.
I haven't figured out how to post the screenshot full sized, and the thumbnail isn't readable..
I did manage to get puppy linux up on the old machine, using puppy pfix-ram so it doesn't mount the partitions, but still can't manage to resize the /dev/sda3 partitio.  I can make it smaller, but it has a maximum size of 7570, and I haven't figured out how to  change that.  the two fat32 partitions will let me change them no problem, but I tried to delete the /dev/sda5 and it wouldn't let me.
I think it's the D: backup drive for the windows, and I can just shrink it down and leave it in place, so I'm not worried about that, but I do need to figure out how to increase the maximum size on the sda3.

---

### Post by Ubun2to on 2012-07-24
> **johnplov said:**
> i left a partition off of the list: /dev/sda6 linux swap 392.15 MiB.
I haven't figured out how to post the screenshot full sized, and the thumbnail isn't readable..
I did manage to get puppy linux up on the old machine, using puppy pfix-ram so it doesn't mount the partitions, but still can't manage to resize the /dev/sda3 partitio.  I can make it smaller, but it has a maximum size of 7570, and I haven't figured out how to  change that.  the two fat32 partitions will let me change them no problem, but I tried to delete the /dev/sda5 and it wouldn't let me.
I think it's the D: backup drive for the windows, and I can just shrink it down and leave it in place, so I'm not worried about that, but I do need to figure out how to increase the maximum size on the sda3.

Are using a live CD? (Not sure if Puppy Linux has them.) If so, use that when editing partitions.
Try unmounting the partitions before editing them.
If you still can't do anything, you might have to wipe the drive and start over (but you should wait until other people give you the green light about wiping the drive-you shouldn't make any rash decisions when dealing with something like this).

---

### Post by johnplov on 2012-07-24
I'm booting with and iso cd of puppy linux 2.15, using the command puppy pfix=ram so it just boots in ram.  The partition with linux is unmounted.  It gives a maximum size and there doesn't seem to be any way of raising the maximum.  I've had trouble getting any other puppy distro or ubuntu to boot up, maybe because there isn't room.
I suppose I could wipe the drive and start over, but I'd rather not.  All I want to do is create enough room so that I can upgrade the Ubuntu. THe four year old version I'm using now works okay, but won't handle Chrome, which I like much more than Firefox.
Thanks for your help

---

### Post by Ubun2to on 2012-07-25
> **johnplov said:**
> I'm booting with and iso cd of puppy linux 2.15, using the command puppy pfix=ram so it just boots in ram.  The partition with linux is unmounted.  It gives a maximum size and there doesn't seem to be any way of raising the maximum.  I've had trouble getting any other puppy distro or ubuntu to boot up, maybe because there isn't room.
I suppose I could wipe the drive and start over, but I'd rather not.  All I want to do is create enough room so that I can upgrade the Ubuntu. THe four year old version I'm using now works okay, but won't handle Chrome, which I like much more than Firefox.
Thanks for your help

Have you resized your Windows partition?

---

### Post by johnplov on 2012-07-27
I got tired of fighting it and got a different computer.  Thanks for the help

---

