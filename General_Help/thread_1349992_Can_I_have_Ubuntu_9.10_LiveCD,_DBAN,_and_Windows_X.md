---
title: "Can I have Ubuntu 9.10 LiveCD, DBAN, and Windows XP CD all on one flash drive?"
date: 2009-12-08
forum: General Help
---

### Post by TheOnlyMrK on 2009-12-08
I hope I made this thread in the right spot... I couldn't think of anywhere else to put it and thought it just barely fit in here because it's asking about moding the Ubuntu LiveCD...

I have a 8GiB flash drive with Ubuntu on it and use it as my "swiss army knife" for when I need to fix someones computer, but I also have to have a DBAN CD and Windows XP CD with me a lot of the times and was wondering if I could have DBAN, Windows XP CD, and Ubuntu 9.10 LiveCD all on the flash drive to where when I boot from the flash drive GRUB (or something similar) could come up asking what I want to use, DBAN, Windows XP, or Ubuntu.
That way I could do something like... Start Ubuntu and use it to read the hard drive of a Windows computer that has a virus and they need to get there files, then I'd restart and select DBAN to wipe the hard drive, and then I'd restart again and select Windows XP and install Windows XP back on their computer. I'm hoping this is possible because I have to do just that tomorrow when I go to visit a friend (except he doesn't have a virus his computer is just very slow, probably because the hard drive is near full) so I offered to do everything for him and get his computer running like it was new.

---

### Post by fluffman86 on 2009-12-08
I know you can do Ubuntu and DBAN, but the WinXP might be a little troublesome.

First, install the Ultimate Boot CD for Windows (ubcd4win).  You'll need a windows computer and a legal copy of windows XP SP2.  That now has an option to put it on a USB drive, along with DBAN and grub4dos.

Then install Ubuntu to the flash drive using System > Admin > USB Startup Disk Creator.  You'll need to edit text.cfg in the syslinux folder that it created and add a new boot entry 'kernel' to boot from.  Point it to grub4dos, which should boot the UBCD4win grub menu, and allow you to select either the UBCD4win or DBAN.

UBCD4win is great for removing viruses because it can read the registry hive on the local machine and scan with all sorts of scanners, including MalwareBytes.  

I'm not sure about the legality of using your XP cd to install on someone else's computer, but in theory Grub4Dos can actually mount an iso file and boot it.  You'll need to look up how to add an entry in grub4dos.

I'll subscribe to this thread, so just post back here if you need more help.  I haven't done this in a while though, so maybe some of the info has changed, but hopefully I've given you some ideas to put you on the right track.

edit: I've also been posting in this similar thread, and you might see some more info there that I left out here:
[http://ubuntuforums.org/showthread.php?t=1346748](http://ubuntuforums.org/showthread.php?t=1346748)

---

