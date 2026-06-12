---
title: "External Hard Drive Sharing Issues"
date: 2011-03-28
forum: General Help
---

### Post by goober0122 on 2011-03-28
Alright, so I have faith that someone here can help me.  I have Ubuntu 10.10 32-bit loaded on one of my PCs.  All of my other machines are Windows 7 64-bit (Ultimate and Professional).  All of my network shares on my Ubuntu machine and working fine, the shares are all on the internal hard drive.

I recently moved my 750gb Western Digital My Book (USB) to my Ubuntu machine.  If the WD is not used for awhile, when I click on it on my desktop it takes a few seconds and I can hear it spinning up.  If I open it back up shortly after using it, it is almost instant.  

I shared a folder on the WD and confirmed I could see it.  I then immediately mapped it as a network drive on one of my Windows 7 machines, everything worked fine.  A few hours later I went to map it on my Windows 7 laptop and Windows said the directory wasn't accessible.  I tried other shares that were on the internal hard drive of the Ubuntu machines and had no issues.  The folder on the WD was listed in the Ubuntu shares, but no matter what I couldn't open it.

I then went to the Ubuntu machine and double clicked on the WD and then went to the share on my laptop.  I could open, read, and write with no issues.

I believe that this is a power management issue in Ubuntu.  I re-created the entire situation, but with the WD connected to my Windows 7 PC.  I let the machine sit idle for a few hours and then tried accessing it from Ubuntu, no issues!  

The Ubuntu machine has no power management enabled that I can see.  I have been using Ubuntu for a few years now and am knowledgeable in configuring it within the GUI, but I haven't had to edit any files or run any commands to fix issues.

If someone could please point me in the right direction, I would really appreciate it!

TLDR: External hard drive goes to "sleep" in Ubuntu and shares on it can't be accessed until Ubuntu "wakes" the external drive up.

---

### Post by seawolf167 on 2011-03-29
I'd check two things:

1. Is the drive being unmounted after a certain amount of time? Or are you logging in/off or restarting between the processes? If so, it would help quite a bit to add an entry in /etc/fstab so the drive is automatically mounted at boot (you may want to do this anyway as manually mounting each time is a pain)

2. As for hard drive spinning down, the drive may have some power-saving feature of it's own that I wouldn't know how to edit, but you can change the way your system handles it by editing the following file

```
nano /etc/hdparm.conf
```

Look for the spindown = XYZ line, then change that to whatever you want. The timing has units of 5 seconds (so 24 = 120 seconds)

There is probably an easier way to do step 2, hopefully someone will chime in

---

### Post by tiki28 on 2011-03-30
I have a similar problem .............but I believe it is a permissions issue, as it will not accept changes to the permission for any other user or group.

---

### Post by svetiev on 2011-06-27
BUMP!

I have the same exact problem, did anyone manage to work this out yet?

---

### Post by svetiev on 2011-06-27
This is a solution I found in another thread:

[http://ubuntuforums.org/showpost.php?p=10017310&postcount=1](http://ubuntuforums.org/showpost.php?p=10017310&postcount=1)

---

### Post by svetiev on 2011-06-28
This solution is still buggy. Put aside the fact that I have to manually unmount the drive as root and then click safely remove drive to completely remove it from the system, once the drive has been accessed via network the samba process keeps it busy so actually none of the above commands can work, so I end up pulling the usb plug while it's still mounted and then I have to clean up the fstab file, manually delete the mount point folder in /media in order to be able to mount the drive again.

It's still a huge pain in the ***. So this solution would only work for an external drive that is meant to be plugged in constantly. 

Any ideas on how to simplify this entire process and achieve full mount unmount functionality?

---

### Post by mcduck on 2011-06-28
> **svetiev said:**
> BUMP!

I have the same exact problem, did anyone manage to work this out yet?

power management (which is the subject of this thread) or permissions (which really doesn't belong here and i sa different issue)?

What comes to the power management, that's a built-in feature of external WD drives and the only solution is to do something to access the drive once every 10 minutes so the power saving doesn't have a change to kick in. 

For permissions, that's related to the filesystem you are using. If possible use a Linux filesystem and you can set the ownerships and permissions of files and directories in the normal way. If you need to use a Widnows filesystem on the drive then it's with fstab (for permanent mounting) or modifying udev rules to mount fat/ntfs drives with the permissions you want (I can't give you exact details how to do that, I don't even have any other FAT drives than a single old USB stick... :D).

edit:
svetiev: easy solution, stop samba first, then unmount the drive. Or try the udev route, although that would still mean having same permissions for every file & directory on the drive as FAT/NTFS simply can't handle anyhting else.

---

