---
title: "USB drive mounting difficulties"
date: 2012-02-25
forum: General Help
---

### Post by iowabeakster on 2012-02-25
I run Xubuntu 10.04 -64bit on a desktop PC.  Two users-- me and my wife.

I have always had some difficulties with USB storage devices.  Not big problems, just hassles and it's time I asked about it.  

1.  I have an external 1 terabyte hard drive, we store photos, documents, and I do system  back-ups (from internal hard drive) on it occasionally.  This drive mounts and gives permission to only one user at a time.  I have tried to manage "Users and Groups" to give permissions to both of us all the time, but I can't figure out how.  It mounts to whoever logs in first after turning on the computer.  Typically we both are logged in.

It's not (wasn't) a big deal.  I could just: switch to her user, unmount it, switch back to my user, and then I can mount it and have permission.  It was a minor hassle that wasted 20-30 seconds.

Today, I couldn't unmount by simply right-clicking.  I got an error "cannot unmount... was probably mounted by command line".  It was NOT mounted by command line... grrrrr... even more of a hassle.

Anyone able to clue me in on how to set-up users and groups so we both can use the external drive... without the annoying user-switching-routine?

2. When I plug my android phone (which has two "drives"... emmc and sdcard) the computer completely randomly chooses which user(s) get permssion when mounted.  For example, my wife's user gets permission for emmc... and I get permission for sdcard (or vice-versa).  Or either user gets mounted and permission for both (again random).    I expect both drives would mount and my user would have permission for both drives, consistently.  The only way that happens if I my wife has not used the computer all day and has not logged on (and that never happens).

I am fairly experienced and comfortable simple command lines, but far from an expert. 

 What is with this completely random mounting and granting permission stuff?  How can I make this do what I expect, instead of randomness?

---

### Post by bab1 on 2012-02-26
> **iowabeakster said:**
> I run Xubuntu 10.04 -64bit on a desktop PC.  Two users-- me and my wife.

I have always had some difficulties with USB storage devices.  Not big problems, just hassles and it's time I asked about it.  

1.  I have an external 1 terabyte hard drive, we store photos, documents, and I do system  back-ups (from internal hard drive) on it occasionally.  This drive mounts and gives permission to only one user at a time.  I have tried to manage "Users and Groups" to give permissions to both of us all the time, but I can't figure out how.  It mounts to whoever logs in first after turning on the computer.  Typically we both are logged in.

Typically external hard drives are formatted with vFat as the file system.  This allows them to be used "out of the box" on most systems.  Ubuntu detects this and should automout the drive in /media with the user that is logged in as the owner and group for the drive.  The file system vFAT does not natively understand users/groups/others as is used by Linux (i.e. with ext2,3,4 Linux file systems).  I believe the user that has logged in first is the one that is enumerated.  
> 

It's not (wasn't) a big deal.  I could just: switch to her user, unmount it, switch back to my user, and then I can mount it and have permission.  It was a minor hassle that wasted 20-30 seconds.
If this drive is permanently connected you could used *fstab * to mount the drive while choosing the user and group you want.  If you use a group that your wife and you are members of and then set the permissions correctly, both of you should be able to use it with no problems > 

Today, I couldn't unmount by simply right-clicking.  I got an error "cannot unmount... was probably mounted by command line".  It was NOT mounted by command line... grrrrr... even more of a hassle.
...or you had a fie in use.  The OS won"t allow you to unmount the partition with a file locked.> 

Anyone able to clue me in on how to set-up users and groups so we both can use the external drive... without the annoying user-switching-routine?
See the man pages for mount, mount.ntfs and fstab```
man mount
man mount.ntfs
man fstab
```
...or you can Google the terms.  We can help you with the specifics after that.> 

2. When I plug my android phone (which has two "drives"... emmc and sdcard) the computer completely randomly chooses which user(s) get permssion when mounted.  For example, my wife's user gets permission for emmc... and I get permission for sdcard (or vice-versa).  Or either user gets mounted and permission for both (again random).    I expect both drives would mount and my user would have permission for both drives, consistently.  The only way that happens if I my wife has not used the computer all day and has not logged on (and that never happens).
Again; this is the result of the way Linux enumerates the devices and users as they are connected.  If you wife has not logged out (has processes running) and you have just switched users the system will be confused as to who connected the device.> 

I am fairly experienced and comfortable simple command lines, but far from an expert. 

 What is with this completely random mounting and granting permission stuff?  How can I make this do what I expect, instead of randomness?
Mostly it's due to the use of vFAT on external media (HDD, SSD and Flash drives).  The reason is that vFAT is the most universally recognised file system (but not necessarily the best).
  
The easiest to overcome this randomness is to have only one user logged on the system any time you are attaching a device.  Another way would be to define the devices in the *fstab *file with "no mount at boot", but you would have to manually mount the device every time you plugged it in.  

I'm sure there is some routine that can be hacked in the auto mount system to achieve this goal, but it's hardly worth the time.

---

### Post by iowabeakster on 2012-02-26
Thank you so much for the reply.  I'm doing some other stuff right now, and will read up on the man pages, as you suggested.  I'll mark it as solved for now, but might change it back, if I need more assistance with the fstab when I start messing with it.

---

