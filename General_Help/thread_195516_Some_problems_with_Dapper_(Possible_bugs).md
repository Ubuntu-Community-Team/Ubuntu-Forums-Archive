---
title: "Some problems with Dapper (Possible bugs)"
date: 2006-06-13
forum: General Help
---

### Post by Xilon on 2006-06-13
I didn't really care about these things but then my dad tried the liveCD and tried installing Ubuntu onto his PC (first time Linux user), and he had a couple of problems with things (whereas I just used the terminal).

First off, one of the more important things... mounting HDDs does not work, neither on the LiveCD nor on an install. I assume that going to Computer, right clicking on a harddrive wanted to mount and selecting Mount Volume is supposed to mount the device... well it doesn't. It seems like it wants a removable device.
Note: The HDD being mounted is an NTFS drive.
[INDENT][IMG]http://img211.imageshack.us/img211/6097/screenshotnautilus0iq.png[/IMG][/INDENT]

Another thing my dad had a problem with was the floppy drive... I can't post any screenshots atm but basically he was unable to write anything to a floppy disk because it kept coming up with an I/O error. We tried multiple floppy discs and none worked. I don't even have a floppy drive so I don't have this problem ;)

Now to my problems... it's pretty much just related to symlinks. I can create a symlink easily, via GUI or terminal, but I can only remove them via terminal. The problem is due to the symlink pointing to a file/directory on a FAT32 filesystem, due to this I'm not sure if it's possible to repair this "bug" but it would be nice since I *can* remove it via terminal. It almost seems like via the GUI it wants to delete the file that the symlink points to. It works fine within linux filesystems
Note: The symlink itself is on a linux filesystem, it just points to a file within a FAT32 system.
[INDENT][IMG]http://img133.imageshack.us/img133/619/screenshotnautilus18zr.png[/IMG][/INDENT]

The last problem is also with symlinks but this time it's about sharing them on a network. The symlink is succesfully made and placed within a shared folder which is accessible and real files are seen on the network. When viewed from a WinXP machine the symlinks (to FAT32 files) are invisble while real files and symlinks within a linux filesystem are visible. Again this problem only exists when a symlink points to a FAT32 file. I did not have this problem on Breezy or when dist-upgrading from Breezy into dapper (before the final release).
[INDENT][IMG]http://img157.imageshack.us/img157/5128/screenshotnautilus4ih.png[/IMG]
[[IMG]http://img106.imageshack.us/img106/2098/screenshotexplorer4bh.th.png[/IMG]](http://img106.imageshack.us/my.php?image=screenshotexplorer4bh.png)[/INDENT]

Imo these problems shouldn't exist, especially the first two since mounting HDDs would be the first thing someone would want to do.

---

