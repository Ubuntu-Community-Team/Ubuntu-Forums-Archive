---
title: "Ubuntu 10.10 won't boot. No init found."
date: 2011-01-16
forum: General Help
---

### Post by lspear76 on 2011-01-16
I was checking my hard drive for errors today on Ubuntu, and there were no errors found. After it was done, my Ubuntu desktop was blank. There was no text on the screen even though I could see my background, menu, etc. When I tried to boot, I get the error that /dev on /root/dev failed, /sys on /root/sys failed, /proc on /root/proc failed. Target filestystem doesn't have sbin/init. No init found.. None of the other restore points boot either, all giving me different errors, including udev trigger is not permitted while udev is unconfigured.

I have Windows XP on hard drive 1, and Ubuntu 10.10 on hard drive 2. 

Right now I'm using Ubuntu with the 10.10 cd. What can I do to fix Ubuntu on hard drive 2 or at least save all of my data?

Help please.

---

### Post by lspear76 on 2011-01-16
At the very least, how can I save my files on that hard drive? I want to save those files before I reinstall Ubuntu 10.10. Are they lost forever?

---

### Post by wilee-nilee on 2011-01-16
> **lspear76 said:**
> **I was checking my hard drive for errors today on Ubuntu, and there were no errors found. **After it was done, my Ubuntu desktop was blank. There was no text on the screen even though I could see my background, menu, etc. When I tried to boot, I get the error that /dev on /root/dev failed, /sys on /root/sys failed, /proc on /root/proc failed. Target filestystem doesn't have sbin/init. No init found.. None of the other restore points boot either, all giving me different errors, including udev trigger is not permitted while udev is unconfigured.

I have Windows XP on hard drive 1, and Ubuntu 10.10 on hard drive 2. 

Right now I'm using Ubuntu with the 10.10 cd. What can I do to fix Ubuntu on hard drive 2 or at least save all of my data?

Help please.

How were you doing this, the highlighted part, and from a live Ubuntu cd run this command and post it.
sudo fdisk -lu

---

### Post by lspear76 on 2011-01-16
> **wilee-nilee said:**
> How were you doing this, the highlighted part, and from a live Ubuntu cd run this command and post it.
sudo fdisk -lu

I was having problems with my computer shutting down somtimes when running too many programs/videos/music. At first I thought it was a problem with Ubuntu but when I'm in Windows XP it does it sometimes too.

Anyway, I looked up some information on these forums to check for hard drive errors and came across fsck so I ran that command in the terminal on the hard drive Ubuntu 10.10 is on. It got to 100% after awhile, fixing a few inodes? in the beginning. Then, with the Ubuntu OS still open, everything I clicked showed no text. I tried to view my web files on localhost (I'm designing a website locally on xampp), and there was a strange error that something was in "read only mode" and I could not view any web files locally on xampp in any browser. I thought this was because the fsck was running, but I guess it was something more severe. 

I tried the live CD thing (both 10.10 and 10.04) but I can't access the hard drive Ubuntu was on. I get all kinds of errors abotu superlocks, and when I try to boot any recovery point, it says Init not found. 

Right now I'm using Recover Data for Linux (that said it didn't find any Linux partition) and when I'm dong i'll post the result of that command.

What a mess.

---

### Post by lspear76 on 2011-01-16
```


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7ea17ea1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625121279   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   625137344   312568641    7  HPFS/NTFS




```sdb1 is Linux, confirmed by gparted. 20.77 gigs used. 277 gigs unused. status = unmounted?

I can't believe this happened. I was going crazy over Ubuntu and how great it was/is. Even bought the fifth edition book. I should have backed up my files. Also, if I have to reinstall xampp, what a nightmare it was to allow my username be the owner of the files in /opt/lampp/htdocs. Was having problems uploading files with php, only to not have permission on them since they're saved to root. I'm trying to learn Linux, but it's been tough.

---

### Post by wilee-nilee on 2011-01-16
So your running a wubi I think you have run the fdisk from a live Ubuntu, both mistakes is this true.

---

### Post by lspear76 on 2011-01-16
Seems too complicated, I don't understand that page. Even though Windows XP sucks, I never had something like this happen with that, especially within 3 weeks of using the operating system. There's gotta be a way to repair the OS without wiping out everything.

---

### Post by lspear76 on 2011-01-16
> **wilee-nilee said:**
> So your running a wubi I think you have run the fdisk from a live Ubuntu, both mistakes is this true.

What's a wubi? I installed Ubuntu 10.10 to my 2nd hard drive, while keeping Windows XP on my first. I agree, I definitely made a mistake somewhere, I can't believe severe enough so cause this. When I ran fsck, at first, it wasn't on the live cd. But trying to fix the problem with a live cd, fsck doesn't seem to do anything. /dev/sdb1 does not respond. I might have tried to run fsck on the windows hard drive, getting the names of the drives mixed up. I don't know. But I can still boot into Windows XP on my first hard drive.

---

### Post by wilee-nilee on 2011-01-16
> **lspear76 said:**
> Seems too complicated, I don't understand that page. Even though Windows XP sucks, I never had something like this happen with that, especially within 3 weeks of using the operating system. There's gotta be a way to repair the OS without wiping out everything.

That was incorrect information actually I missed the NTFS housing the Ubuntu. So you ran the fdisk in the live wubi correct?

We have to keep a close watch out for helping as users don't name the setup and it is easy to miss it, at times.

Always mention the type of install, if you can it will help you and the help.:)

---

### Post by wilee-nilee on 2011-01-16
> **lspear76 said:**
> What's a wubi? I installed Ubuntu 10.10 to my 2nd hard drive, while keeping Windows XP on my first. I agree, I definitely made a mistake somewhere, I can't believe severe enough so cause this. When I ran fsck, at first, it wasn't on the live cd. But trying to fix the problem with a live cd, fsck doesn't seem to do anything. /dev/sdb1 does not respond. I might have tried to run fsck on the windows hard drive, getting the names of the drives mixed up. I don't know. But I can still boot into Windows XP on my first hard drive.

```
  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   625137344   312568641    7  HPFS/NTFS
```

That is the whole HD and it says NTFS, Ubuntu will only install to a NTFS if it is a wubi or a virtual, basically. Wubi=install from a live windows environment, looks like you did this installing to sdb.

You at least read as a ntfs now, boot a Ubuntu cd and open gparted to look at sdb. There is a dropdown in the top right corner for choosing the drives to look at. Take a screen shot of it and post it, both HD's preferably.

---

### Post by lspear76 on 2011-01-16
Here you go. I don't understand what you mean by a windows environment? I formatted this 2nd hard drive and installed Ubuntu 10.10 on it. It used to have some windows file on it, but I cleaned them all out before I installed Ubuntu. I only have Windows XP on the first hard drive.

---

### Post by wilee-nilee on 2011-01-16
> **lspear76 said:**
> Here you go. I don't understand what you mean by a windows environment? I formatted this 2nd hard drive and installed Ubuntu 10.10 on it. It used to have some windows file on it, but I cleaned them all out before I installed Ubuntu. I only have Windows XP on the first hard drive.

sdb says linux for a name, but is a NTFS. A live windows enviroment=a running XP that you installed Ubuntu from. At least that is what it looks like and I do this every day and use open source mainly but have XP and W7 I'm not blowing steam up your er well...

So at this point you will have to access the Ubuntu install if it is possible from XP. Does or didn't the sdb drive show in the XP computer section.

---

### Post by wilee-nilee on 2011-01-16
If you need proof of the wubi, run the bootscript link in my signature. Post it if needed, in code tags. Run the script from the Live Ubuntu cd.

---

### Post by lspear76 on 2011-01-16
The label says Linux, I named the hard drive Linux once I cleared everything off of it. This was originally my 2nd hard drive for Windows XP, used to just store files I didn't have room for. Before I installed Linux, I moved those files to another hard drive. Maybe I didn't install Ubuntu correctly? I just put the disc in and it asked me what hard drive and I picked the one that didn't have my Windows XP operating system on it. I've been using Ubuntu that way since I installed it three weeks ago. That's incorrect?

---

### Post by lspear76 on 2011-01-16
```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdb1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   625,121,279   625,121,217   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       4a2ea476-f658-47a2-acbf-7ae970b46175   ext4                                     
/dev/sda1        945C11395C111796                       ntfs       XP                            
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0214E58914E58051                       ntfs       Linux                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /usepmtimer /NoExecute=OptIn 
C:\wubildr.mbr = "Ubuntu"


```

---

### Post by wilee-nilee on 2011-01-16
> **lspear76 said:**
> The label says Linux, I named the hard drive Linux once I cleared everything off of it. This was originally my 2nd hard drive for Windows XP, used to just store files I didn't have room for. Before I installed Linux, I moved those files to another hard drive. Maybe I didn't install Ubuntu correctly? I just put the disc in and it asked me what hard drive and I picked the one that didn't have my Windows XP operating system on it. I've been using Ubuntu that way since I installed it three weeks ago. That's incorrect?

You put the disc in while running XP correct can we at the least confirm this.

If this correct it is just another way of installing, but has limited use. Not good for learning code commands when installed this way, it is just a file inside XP. generally this is a method for trying Ubuntu and if you like it then booting the live cd of Ubuntu and installing, or transferring a working wubi to a partition. Linux uses ext type partitions, like they look in my  gparted, here my gparted with W7 and 3 Linux distros.
[ATTACH]181285[/ATTACH]

---

### Post by wilee-nilee on 2011-01-16
sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:  [B] /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk
[/B]

sdb1/**Wubi**: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

This is what a wubi looks like.

So it is hard to say if it is salvageable as a bootable OS now, maybe I'm not a wubi user. On the sdb is a Ubuntu file all your stuff is there probably, you will have to use the live cd to get there. Problem is that the live cd isn't reading the sda HD, notice the red button on the gparted screen shot on sda1, this if right clicked and then information will give you a general problem and solution.

As I say I'm not a wubi user but there are a couple regulars that might have some answers. If you run a chkdsk on the XP it will mess with the already broken install on sdb, so don't just act without some sound advice.

It looks like the sdb drive is readable from the live Ubuntu cd so I don't know if you can navigate to the wubi and get your stuff out that way if needed.

---

### Post by lspear76 on 2011-01-16
I don't think I put the disc in while XP was on. I meant to install it fresh on this hard drive by itself. I burned the 10.10 disc from the website and followed the instructions.

Anyway, this is pretty messed up. This makes me think twice about using Ubuntu anymore. Now I have to reinstall the OS, xampp, change those permissions again, rewrite all my website files I didn't think about backing up. I only used Ubuntu 3 weeks anyway. What a mess. Should have stuck with Windows. :(

Thanks for trying to help... one last thing. What's the proper way to install Ubuntu from the 10.10 disc without it being tied to Windows?

---

### Post by wilee-nilee on 2011-01-16
> **lspear76 said:**
> I don't think I put the disc in while XP was on. I meant to install it fresh on this hard drive by itself. I burned the 10.10 disc from the website and followed the instructions.

Anyway, this is pretty messed up. This makes me think twice about using Ubuntu anymore. Now I have to reinstall the OS, xampp, change those permissions again, rewrite all my website files I didn't think about backing up. I only used Ubuntu 3 weeks anyway. What a mess. Should have stuck with Windows. :(

Thanks for trying to help... one last thing. What's the proper way to install Ubuntu from the 10.10 disc without it being tied to Windows?

The best way would be to make sure you remove all the wubi first; which is probably in the control panel in XP under add remove programs, in the admin account. Don't just overwrite sdb wth out removing wubi first, the wubi=Ubuntu boot will still be in your MS startup other wise.

For the safest install I would unplug the sda drive boot the Ubuntu cd and install it to the whole sdb drive or partition it ahead. You can get quick help on the forums for installs.

Your experience is like others even my own to some extent. Just a series of user errors, it happens to all of us.:)

**I think you need to run a chkdsk /f/r in XP as well after removing the wubi, do you know how to do this?**

---

### Post by lspear76 on 2011-01-16
I ran a checkdisk on my C drive. But the wubi was on the 2nd drive. I guess i'll run a check on that one too. But that one is sata. How do i run a chkdsk on the 2nd hard drive?

Another thing -- my 2nd hard drive is formatted as ntfs. I tried to reformat it but windows won't let me. Do i have to reformat it to the proper structure before trying to install Ubuntu to it?

---

### Post by wilee-nilee on 2011-01-17
> **lspear76 said:**
> I ran a checkdisk on my C drive. But the wubi was on the 2nd drive. I guess i'll run a check on that one too. But that one is sata. How do i run a chkdsk on the 2nd hard drive?

Another thing -- my 2nd hard drive is formatted as ntfs. I tried to reformat it but windows won't let me. Do i have to reformat it to the proper structure before trying to install Ubuntu to it?

 Did you remove the wubi from add remove, and is the Ubuntu removed from the MS boot? 

If the sdb is empty you can reformat the whole thing from the live Ubuntu cd using gparted. The windows partitioner will not build the ext4 partition, or a swap like you see in my gparted screen shot.

Since you have these two drives you can set up the second HD=sdb to have a backup image/images of the C in XP on it and the Ubuntu installation as well. does this sound like a plan you might want? This could also be a shared NTFS partition that both XP and Ubuntu can read and write to.

I ask so that we can get you all set up clean and having the full use of both OS and backups saved of the full XP, if you want.

We want to make sure XP is mountable from the live cd, it may be that you can recover some of the Wubi if you haven't removed it.

---

### Post by lspear76 on 2011-01-17
I removed Ubuntu from the C: drive and ran chkdsk on both drives to make sure everything was okay.

I wrote down which drive was what so I wouldn't make the same mistake again. 

This time, the installation was different, with steps I don't remember from last time, and I made sure to select "use the whole disk" and not "run alongside another OS". It seems as if Ubuntu was installed correctly on my 2nd hard drive, in the correct non ntfs format. The boot up screen is different too. Before it took me to Windows XP/Ubuntu and then another menu. Now it just takes me to the Ubuntu/Recovery/Windows XP menu. It looks like everything is working properly now.

I wanted to thank you for talking me through this problem. I would have never really known I installed Ubuntu alongside XP if this wouldn't have happened. At the very least I understand this a little better now. Now I just have to reinstall xampp and get those permissions right so I can access the files stored in /opt/htdocs. Then I have to write my code over again for my website (I installed Linux mainly for a localhost to develop php pages). I should have backed up those files, but I know better now. 

I'm not sure about the options you mentioned for XP, or quite sure how to back up the OS. Right now I'm at a fresh install of  Ubuntu on my sata drive, and XP Professional on the regular IDE hard drive.

---

### Post by lspear76 on 2011-01-17
It appears to be installed correctly, the disk utility information now looks correct, unlike before.

---

### Post by wilee-nilee on 2011-01-17
> **lspear76 said:**
> It appears to be installed correctly, the disk utility information now looks correct, unlike before.

You have got it looks like, good job, it is confusing at first. So you must have the sdb drive first in the bios that is correct. So I assume the grub bootloader went to the sdb hd's mbr, you can check by just trying to boot the sda by changing the bios to it being first read, and seeing if the MS boots straight in.

---

### Post by wilee-nilee on 2011-01-17
Here is a link to a Linux based imager or cloning program. You could clone the basic XP set up or whole C partition compressed to a folder on the Ubuntu setup. You then if needed would boot a cd from clonezilla, and you could reimage or restore XP with that image/backup.
[http://clonezilla.org/](http://clonezilla.org/)

There are a number of imaging/backup programs for MS setups, some are free, most I think cost money. You just want to really have a external drive for a back up of a image and extra media you can't loose.

Xp even the home version can be loaded with a MS backup tool that is on any XP disc, as well. This will backup the whole C to a NTFS, whereas clonezilla will back up to a MS NTFS or a Fat32 or a Linux ext type partition.

While I was waiting for your last response, I reloaded my W7 image/backup I had saved, just to make sure it was a good backup.

---

### Post by tk189 on 2011-01-18
I've had this same error time and time again first in 10.04 and less so but still occasionally using 10.10

Does it also say something about Passing Bootarg after the no init part?

The only thing that i could find to fix it was to run a LiveCD session and chroot into the HDD to purge and re-install the grub bootloader. Being unable to boot into the os proper I had to use the cd and then change root.

For some reason (still unknown) grub seems to 'forget' if that's an appropriate term where the operating system is installed. How very useful of it...

I have followed this [walkthrough guide to purge and re-install grub]("http://ubuntuforums.org/showthread.php?t=1581099") (Be prepared to end up doing this daily however. Great huh?) so many times now I just want to scream and give up on ubuntu totally but for some reason my hatred of Windows prevents me from doing so.

That said, several other problems with ubuntu 10.10 freezing up, crashing etc etc are making me look elsewhere.

---

