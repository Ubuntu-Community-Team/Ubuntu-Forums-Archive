---
title: "Phantom Directory"
date: 2010-10-25
forum: General Help
---

### Post by mcedata on 2010-10-25
OK, thought I had Ubuntu all figured out. Nope.

I use an external REV drive.  When I put a cart in the drive, Ubuntu recognizes it as 1-Backup Set A. I can view the contents, write to it, and so on.

When I look in the Ubuntu file system, under /media, a directory named 1-Backup Set A is created when the cart is loaded, and it goes away when the cart is removed. All normal so far.

Also under /media is a directory named 1-Backup Set D. Loading or unloading a cart in the REV drive has no effect on this one... just sits there...and it's empty.  If I look at it with "computer" and go into the file system and check it's properties, it shows contents "nothing", free space "unknown". If I look at it via Dolphin, it has 48.7Gib free of 70.5GiB...which are the stats from the single hard drive installed. WTF?  In addition, I can find no way to delete that directory...I get no response when trying to delete it from Computer, and "permission denied" when trying to sudo it from a command line.

And now, when I use Simple Backup, although SB is configured to send the backup to 1-Backup Set A, the backup goes into the 1-Backup Set A directory, but not onto the REV cart. This has worked properly for months, and worked as lately as last week. The REV drive is OK, since it works just fine with writing and deleting stuff, and works OK when plugged into an adjacent Windows (shudder!) machine.

Any suggestions as to what's up with this? I'm totally baffled.

Thanks for any help,

Steve

---

