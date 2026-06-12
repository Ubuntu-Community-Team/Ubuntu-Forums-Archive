---
title: "Is This A Bad Idea?"
date: 2010-12-06
forum: General Help
---

### Post by apocalypsemystic on 2010-12-06
So I've been working on [this]("http://ubuntuforums.org/showthread.php?p=10205232#post10205232") problem without much success and at this point I just want to get my computer back online. I'm a bit new to linux so I wanted to check before I did anything. I'm thinking about just reinstalling from my cd. If I do this, I have a few questions:

1) Is it possible to just reinstall root and leave my home (my files I presume) alone? The files are backed up but if I can just recover usability and hold onto the files all the better.

2) If 1 is possible, what does one lose by reinstalling the root segment

3) Is it possible to try any less invasive actions first like reinstalling GRUB or something? My linux is on a logical partition and shares physical space with windows vista, so idk how they interact and whose boot stuff is where

4) No holds barred, hell with the data, what's the best way to just get my system back up? Thanks.


EDIT: Using the system restore cd and e2fsck -p I was able to repair my root and it might even have worked but I accidentally deleted my mac partition and everything fell apart from there. Clean install. Working fine.

---

### Post by coffeecat on 2010-12-06
Looking at your original thread, I don't know what else you can do to successfully repair the filesystem on sda5. So...

> **apocalypsemystic said:**
> 1) Is it possible to just reinstall root and leave my home (my files I presume) alone? The files are backed up but if I can just recover usability and hold onto the files all the better.

Is your /home on sda6? If so, you could choose the manual option at the partitioning stage of the installer. Point the installer to sda5 for root (mountpoint = /) and tell it to reformat. Point it to sda6 for /home and, obviously, make sure it is not set to reformat.

> **apocalypsemystic said:**
>  2) If 1 is possible, what does one lose by reinstalling the root segment

All of your installed applications. You don't lose your personal settings for apps because they are stored in hidden files and folders in your home.

> **apocalypsemystic said:**
> 3) Is it possible to try any less invasive actions first like reinstalling GRUB or something? My linux is on a logical partition and shares physical space with windows vista, so idk how they interact and whose boot stuff is where

Your sda5 fileystem is corrupted and nothing short of repairing it will suffice, but you've already tried that. Re-installing Ubuntu to sda5 will cause grub to be reinstalled so you should end up with a grub dual-boot menu for Vista as well.

> **apocalypsemystic said:**
> 4) No holds barred, hell with the data, what's the best way to just get my system back up? Thanks.

If sda6 is your /home partition and if sda6 is clean, your data should be fine. If sda6 is corrupted, then reinstall Ubuntu and use the space in sda5 and sda6 combined in whatever way you see fit.

By the way, I've no experience of setting up Ubuntu on a Mac with a Bootcamped Windows, so I don't know how grub interacts with the Mac boot menu. Or does grub replace that? So my comments about grub and Vista dual-boot may be off-beam. But your central problem is a corrupted filesystem on sda5. If that can't be repaired you need to reinstall.

One other comment - if you've decided to reinstall, please post on your other thread saying so, linking to this thread.

---

### Post by apocalypsemystic on 2010-12-06
Thanks. That's what I'll try. Do you know is there any way to easily find a list of the applications I had installed so I can redownload them at once? Thanks.

---

### Post by searchfgold6789 on 2010-12-06
> **apocalypsemystic said:**
> Thanks. That's what I'll try. Do you know is there any way to easily find a list of the applications I had installed so I can redownload them at once? Thanks.
[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

---

### Post by apocalypsemystic on 2010-12-06
Thanks. I've always wanted to know how to do that. Unfortunately now the live cd stalls after either 'try ubuntu' or 'install ubuntu.' I was running live just fine the other day and I originally installed from this disk. Not really sure where to start with this one x / Back to google.

---

