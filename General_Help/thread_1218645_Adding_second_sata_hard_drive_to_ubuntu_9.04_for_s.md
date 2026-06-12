---
title: "Adding second sata hard drive to ubuntu 9.04 for storage?"
date: 2009-07-20
forum: General Help
---

### Post by SirWeazel on 2009-07-20
Adding second sata hard drive to ubuntu 9.04 for storage?

I've already formatted the drive with Gparted. Drive is formatted as ext3, primary partition, and labeled as "Data". When i click on "places" i can see the Drive, and when i click on it the drive mounts. It opens File Browser with the directory "lost+found".  I am unable to do anything with it.  I think permissions are sett incorrectly, maybe as "root" but i'm new to ubuntu/linux.  I want this drive to be shared with the other Ubuntu user accounts on my box also and not just my account. I found a walk thru for older version of ubuntu using terminal, but i havn't tried yet because i was unsure because it was for an older version.  Also if there is a step by step graphical way of doing it i would prefer this method - so in the future i can walk someone thru the steps easily over the phone.  I plan on installing more ubuntu desktops for friends and family, so as i learn i am learning for myself and others.

Thank you in advance for any help given, i hope to contribute my knowledge one day in the future.

Also, can i have a drive/folder & Printers shared when i turn on my computer without logging into ubuntu user account? Or do i have to logg into my ubuntu account before i can access shared stuff from another computer.. Not sure if this question is related to above Permission ownership thing or not. Thanks again for any input.... Newbie trying to learn... Yes i am the FNG :)

---

### Post by michy99 on 2009-07-20
See if this is any help to you:

[http://helpforlinux.blogspot.com/2008/09/auto-mount-hard-drives-on-ubuntu.html](http://helpforlinux.blogspot.com/2008/09/auto-mount-hard-drives-on-ubuntu.html)

---

### Post by SirWeazel on 2009-07-21
Yes thank you, that did the trick. I also used used this set of instructions i found in another thread ([http://ubuntuforums.org/showthread.php?t=717149&page=2](http://ubuntuforums.org/showthread.php?t=717149&page=2)) that helped also:
alt-f2
gksudo nautilus /media
right click > properties on each of the drives I wanted
permissions tab
set owner to myself
set group to users
both with create/delete folder access
closed
refreshed nautilus as my user, and immediately had access.
NEVER do this to anything but media disks that you want accessible and shared by. 

Once again, thank you for your quick post.

---

