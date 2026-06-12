---
title: "Can't mount Wubi files from new Ubuntu install"
date: 2010-04-23
forum: General Help
---

### Post by scoobeee on 2010-04-23
I tried out Wubi or a few months last year and liked it but after the second time having [this problem]("http://ubuntuforums.org/showthread.php?t=1339203&highlight=can't+mount+wubi+files") with grub I could no longer boot into Wubi. I recently shrunk my windows partition and installed Ubuntu for real and would love to recover my files, apps and settings from that wubi install. However I can't mount the wubi root.disk while in Ubuntu and am fairly lost at this point. Here is my [boot info results]("http://docs.google.com/View?id=d7sdpnt_169d9s6sqgw") which I don't really what to do with. Attempting to mount results in "wrong fs type" or 

[INDENT]Failed to read bootsector (size=0)
Failed to mount '/media/19E452EA62FBAD4C/ubuntu/disks/root.disk': Invalid argument
The device '/media/19E452EA62FBAD4C/ubuntu/disks/root.disk' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?[/INDENT]

---

### Post by bcbc on 2010-04-24
You should be able to mount the old wubi. I've done it.

```
sudo mkdir /media/oldwubi
sudo mount /media/19E452EA62FBAD4C/ubuntu/disks/root.disk /media/oldwubi -o loop
```

Edit: PS if you want to boot the old wubi you probably just need to replace the wubildr file. See [here]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

---

