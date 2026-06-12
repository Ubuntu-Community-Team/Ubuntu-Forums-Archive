---
title: "Odd drive naming problems"
date: 2011-11-05
forum: General Help
---

### Post by zcacogp on 2011-11-05
Hello. 

I have been changing around the names of my drives recently, and for some reason the old names of the drives still appear in Nautilus - despite the drive name having been changed in fstab. 

An example of this is shown in this screenshot; 

[IMG]http://i76.photobucket.com/albums/j14/zcacogp/Screenshotat2011-11-05222502.png[/IMG]

Here you can see the directories which exist below /media (Helena, HelenaS, Ianthe, IantheS, Pharmacy, PharmacyS) from the list in the lower right hand side of the screen but you can also see on the upper right hand side of the screen that nautilus thinks there is a path called /media/Ianthe2/Images/... 

Ianthe2 is what the drive that is now called Ianthe was called, but I have taken out all reference to it in fstab. The fstab file now looks like this; 

```
# Samsung (older) drive

# UUID=1d588936-4308-4e8d-9ad8-9c0ba6cf118f /media/HelenaS ext4 defaults 0 0
# UUID=728c678a-4bf6-4c78-8cb2-30b61d9be26f /media/IantheS ext4 defaults 0 0
# UUID=52C399D625D0301D                     /media/PharmacyS ntfs defaults 0 0

# Hitachi (newer) drive

UUID=8642a4da-ebcc-42d6-8578-a46d2d75843b /media/Helena ext4 defaults 0 0 
UUID=2c6d4a49-3311-44ef-8d8b-f297ba425417 /media/Ianthe ext4 defaults 0 0 
UUID=3AAFED7A620FE16A                     /media/Pharmacy ntfs defaults 0 0


#/dev/sr0 /media/cdrom  auto  user,noauto,exec,utf8  0  0

#/dev/sr0 /media/dvd  udf,iso9660 defaults,noauto,rw,user   0 0

/dev/sr0	/media/dvd	udf,iso9660	defaults,noauto,ro,user	0	0
```

You can see that everything is done by UUID, and I have two HHD's in the machine. I want to mount everything from the Hitachi drive as Ianthe, Helena and Pharmacy, and have commended out the mountings of the partitions from the Samsung drive. 

By my understanding, this shouldn't be able to happen - the screenshot of Nautilus shouldn't be possible. What has gone wrong? 

All suggestions welcome - thanks. 


Oli.

---

### Post by lechien73 on 2011-11-05
Interesting one! Does the workaround at [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130) help at all?

---

### Post by DapperMe17 on 2011-11-05
Make it easy on yourself....download and run "disk utility" from the repos!

You can easily change drive names with the GUI.

---

### Post by lolpenguin on 2011-11-05
The problem might be that Nautilus is still trying to find the old drives. Try unmounting/ejecting them?

---

### Post by dcstar on 2011-11-06
> **zcacogp said:**
> 
.........
You can see that everything is done by UUID, and I have two HHD's in the machine. I want to mount everything from the Hitachi drive as Ianthe, Helena and Pharmacy, and have commended out the mountings of the partitions from the Samsung drive. 

By my understanding, this shouldn't be able to happen - the screenshot of Nautilus shouldn't be possible. What has gone wrong? 

All suggestions welcome - thanks. 

Oli.

You should never, **ever** use /media in the fstab file. /media is a system folder used by things like Nautilus, it is not for users to mount things at system level. Put them in /mnt or somewhere else (but not any system folders).

The problem you have is exactly because you are using /media inappropriately.

---

### Post by zcacogp on 2011-11-06
Dear all, 

Many thanks for your replies. For what it's worth, I have just booted the machine for the first time since starting this thread and it has mounted the drives differently again. Besides the fact that it is unusual, it is actually quite difficult for me to know which drive is which, and I need to tell them apart ... 

Lechien, thanks, I'll try that workaround. DapperMe - OK, and thanks for the recommendation. Lolpenguin, I have tried unmounting and ejecting them and to no avail. I've also tried logging out and in again, and turning the machine off and on again; all equally fruitless! Thanks for the suggestion though. 

dcstar - thanks. That is the first time I have heard that /media shouldn't be used in this way. (Indeed, having read the guide to fstab - here: 

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

... it says that the default location is /media for mounting partitions.) I'll try swapping everything to /mnt, but this will surely mean that they won't show up in the Unity taskbar? Why is the behaviour different when using /media to /mnt, and what is the danger of using /media? 

Thanks for your input. 


Oli.

---

### Post by zcacogp on 2011-11-06
Dear all, 

Ok, some progress on this one. It dawned on me that partitions have names, and these are given in the Disk Utility. I had used this to name some drives in ways that conflicted with what I thought I was doing in fstab, and this was causing some of (well, most of) the problems. Re-naming them in the Disk Utility has helped a lot. 

The only remaining problem comes from the fact that, if you have a partition on any of the drives, it appears in the 'Devices' area of nautilus *even if it isn't mentioned in fstab*. If you click on it, it then mounts in /media, and it seems that a temporary directory is created below /media to accomodate it. This is done automatically by Ubuntu - I guess it is meant to be a convenience, but is there any way to suppress this behaviour? (It's not a problem, but I'd rather some of these devices weren't visible at all.) 

dcstar, thanks again for your comments. Can you expand a little on why mounting in /media is such a bad idea? I tried mounting everything in /mnt instead of /media, and while it worked, it meant that none of the drives appeared in the 'Devices' section on the top left hand side of nautilus, and the only way to access them was to navigate to /mnt and work down from there - which isn't very convenient. Mounting them in /media makes for a much more usable system, but I am concerned by your comments that this is undesirable. What problems can it cause? 

Thanks again for your input. I'm going to mark this one as solved. 


Oli.

---

### Post by zcacogp on 2011-11-07
Hello, 

Having thought about my last post, it occured to me that the answer to the problem of hiding partitions that are listed in 'Devices' is to mount them under /mnt. Having done this, I can now see all the partitions I want to have readily accessible under 'Devices' by mounting them in /media, and the ones that I don't want readily accessible are mounted under /mnt and therefore appear to be hidden! 

Thanks for your input. 


Oli.

---

### Post by mcduck on 2011-11-07
> **dcstar said:**
> You should never, **ever** use /media in the fstab file. /media is a system folder used by things like Nautilus, it is not for users to mount things at system level. Put them in /mnt or somewhere else (but not any system folders).

The problem you have is exactly because you are using /media inappropriately.

It's perfectly safe to mount your own files inside /media using fstab. It doesn't cause any problems, and the only reason why you might not want to do it is that the drives will appear in Nautilus bookmarks and on desktop (depending on your settings).

Of course you have to mount the drives *inside* /media, not into /media itself. But apart from that, I'd be interested in hearing if you actually know any reason why mounting something inside /media could cause problems?

For the OP's problem: it seems simply that you didn't remove the old mount points. Editing fstab will not delete the old directories for you, and with filesystems mounted using fstab the mount point creation/deletion is up to the user, it's not handled on-the-fly like with automounting.

---

### Post by mcduck on 2011-11-07
> **zcacogp said:**
> Hello, 

Having thought about my last post, it occured to me that the answer to the problem of hiding partitions that are listed in 'Devices' is to mount them under /mnt. Having done this, I can now see all the partitions I want to have readily accessible under 'Devices' by mounting them in /media, and the ones that I don't want readily accessible are mounted under /mnt and therefore appear to be hidden! 

Thanks for your input. 


Oli.

You don't really even need to mount a drive to stop it from being handled by the automount system, simply defining the drive in fstab is enough. Just add "noauto" to the mount options if you want to define settings for a drive without actually mounting it automatically on boot. Or "user, noauto" if you want normal users to be able to mount the drive in question when needed.

---

### Post by zcacogp on 2011-11-07
McDuck, 

Thanks - for this and for help you have offered me on other threads. 

I think I am there with it now, but the idea of using noauto is a good one - and not one that I had thought of. I can see that the options available in fstab are very useful, and I would do well to learn more about them. 

Thanks for your help. 


Oli.

---

