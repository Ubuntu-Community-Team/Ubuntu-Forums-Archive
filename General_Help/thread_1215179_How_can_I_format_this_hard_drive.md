---
title: "How can I format this hard drive?"
date: 2009-07-16
forum: General Help
---

### Post by magh-87 on 2009-07-16
Hello,

A few months ago I "volunteered" one of my external hard drives to my girlfriend so she could back up her Mac book data before she installed Ubuntu on her system. Now that she has her own external hard drive now and has her dual boot set up, I can finally reclaim my hard drive from her.

The issue is that for whatever reason, I cannot format the hard drive. Ubuntu does not recognize the file system but it does see that it is a Time Machine Backup drive. The only option provided to me by GParted is to unmount it the drive.

How can I format this hard drive so I can use it on my dual booting Windows/Ubuntu machine?

Thanks for any help!

---

### Post by starcraft.man on 2009-07-16
That's puzzling. [Gparted]("http://gparted.sourceforge.net/features.php") says it supports both hfs and hfs+ (for detection. Does time machine do something special to a drive? I know not, I don't use macs.

I'd try again with gparted. I don't see why you wouldn't be able to delete it. Can you just make a new partition table? Device > partition table, that will wipe the selected drive of all data effectively.

If that fails to work, there's always the old reliable, [DBAN]("http://www.dban.org/")! Just download and nuke. Once it's all gone you can make a new partition table and partition as you like.

---

### Post by magh-87 on 2009-07-17
> **starcraft.man said:**
> That's puzzling. [Gparted]("http://gparted.sourceforge.net/features.php") says it supports both hfs and hfs+ (for detection. Does time machine do something special to a drive? I know not, I don't use macs.

I'd try again with gparted. I don't see why you wouldn't be able to delete it. Can you just make a new partition table? Device > partition table, that will wipe the selected drive of all data effectively.

If that fails to work, there's always the old reliable, [DBAN]("http://www.dban.org/")! Just download and nuke. Once it's all gone you can make a new partition table and partition as you like.

Now this is interesting. Since I made the new table, after resetting the drive, my computer is no longer able to recognize it. Everything is plugged in like it was but it won't acknowledge that it's any sort of device.

---

### Post by magh-87 on 2009-07-17
Aha! While frustrating that I had to do this, my windows side was able to recognize the external device and I'm currently using Computer Management to format it to NTFS again.

Any possible reason why Windows was able to do this and Linux could not? It just seems strange to me since I thought that Linux was the best of both worlds

---

### Post by raymondh on 2009-07-17
> **magh-87 said:**
> Hello,

A few months ago I "volunteered" one of my external hard drives to my girlfriend so she could back up her Mac book data before she installed Ubuntu on her system. Now that she has her own external hard drive now and has her dual boot set up, I can finally reclaim my hard drive from her.

The issue is that for whatever reason, I cannot format the hard drive. Ubuntu does not recognize the file system but it does see that it is a Time Machine Backup drive. The only option provided to me by GParted is to unmount it the drive.

How can I format this hard drive so I can use it on my dual booting Windows/Ubuntu machine?

Thanks for any help!

You need to UNMOUNT the external first and then go back and select the drive again?

---

### Post by magh-87 on 2009-07-17
> **raymondhenson said:**
> You need to UNMOUNT the external first and then go back and select the drive again?

That wasn't the case. I was turning the hard drive off/on between boots between sides. I turned the computer and hard drive off, then turned the computer on then the hard drive and still nothing.

---

### Post by raymondh on 2009-07-17
> **magh-87 said:**
>  then turned the computer on then the hard drive and still nothing.

From post # 1, am assuming you were using gparted from your ubuntu install and not a liveCD.

When you turned the computer on and then turned on the external, Ubuntu will mount the external.   That is one reason why (from your first post) the only option you had was to "unmount".  Gparted will not work on any drive or partition that is mounted. 

[http://www.ubuntugeek.com/noobie.html](http://www.ubuntugeek.com/noobie.html)
[http://www.mattcutts.com/blog/format-external-drive-for-linux/](http://www.mattcutts.com/blog/format-external-drive-for-linux/)
[http://ubuntuforums.org/showthread.php?t=468212](http://ubuntuforums.org/showthread.php?t=468212)

Congratulations on being able to reformat it.

---

### Post by magh-87 on 2009-07-17
> **raymondhenson said:**
> From post # 1, am assuming you were using gparted from your ubuntu install and not a liveCD.

When you turned the computer on and then turned on the external, Ubuntu will mount the external.   That is one reason why (from your first post) the only option you had was to "unmount".  Gparted will not work on any drive or partition that is mounted. 

[http://www.ubuntugeek.com/noobie.html](http://www.ubuntugeek.com/noobie.html)
[http://www.mattcutts.com/blog/format-external-drive-for-linux/](http://www.mattcutts.com/blog/format-external-drive-for-linux/)
[http://ubuntuforums.org/showthread.php?t=468212](http://ubuntuforums.org/showthread.php?t=468212)

Congratulations on being able to reformat it.

Awesome, thanks for the help. I guess I was missing a step here,

> Well... I know it will sound like the most stupid idea ever...
but when I want to format my usb stick or memory cards I launch Gparted,
select the drive from the drop-down list on the top left corner,
right click -> unmount drive and right click again -> format to... fat32

I guess Windows still has a use other than games :)

---

### Post by raymondh on 2009-07-17
> **magh-87 said:**
> Awesome, thanks for the help. I guess I was missing a step here,

You're welcome.  Happy Ubuntu-ing :)

---

### Post by matyasfalvi on 2009-07-19
Thanx raymondhenson, I had the same problem for a minute there!
:DDD

---

