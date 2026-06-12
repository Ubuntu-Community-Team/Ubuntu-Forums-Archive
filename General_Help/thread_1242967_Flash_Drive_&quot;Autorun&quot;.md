---
title: "Flash Drive &quot;Autorun&quot;?"
date: 2009-08-17
forum: General Help
---

### Post by derekboy on 2009-08-17
Is there a way to autorun a .SH file in the root of a Flash drive when I insert it into my computer? I know how to do this on Windows, but I didn't know if it also applied to *nix?

---

### Post by Revolutionary101 on 2009-08-17
This link might help you test these commands out. I personally use the command ICON and that works so that means that Linux at least recognizes the autorun file.
[http://www.samlogic.net/articles/autorun-commands.htm](http://www.samlogic.net/articles/autorun-commands.htm)

---

### Post by derekboy on 2009-08-18
I think it would be awesome if you could have an autorun.inf file in your flash drive, and depending on if you are using Windows or *nix, it would run different files (a shell for *nix, a batch or exe for Windows).

**EDIT:**
In [this]("http://usalug.org/phpBB2/viewtopic.php?p=87212&sid=8be1223fb1981d172cc94464cc2094c6") thread, I found a program simply called "[autorun]("http://sourceforge.net/projects/autorun/")", which is described as 
> automagically recognizes all available CDROMs in the system, mounts them upon insertion of a media and executes a possible autorun executable on the CD. The user can remove the media; autorun will call unmount after that.

In the thread that I found the link in, "nukes" states that "I know it says cd, but to the system there's no difference between a file, hard disk, flash drive or ramdisk"

Also, he says 
> Thinking about it some more... If you use like a dockapp or something to mount/unmount your disks, there should be an option for "run command after mount" or command to run.
you could just do: 

mount /mnt/flash && sh /mnt/flash/autorun.sh

---

