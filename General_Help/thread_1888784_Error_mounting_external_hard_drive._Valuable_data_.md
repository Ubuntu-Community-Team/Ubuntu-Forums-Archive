---
title: "Error mounting external hard drive. Valuable data trapped."
date: 2011-11-30
forum: General Help
---

### Post by hitchhiker4242 on 2011-11-30
Since my laptop's HD was full I decided to convert my music library (which is lossless FLAC) into 500 kbps OGG. Using the Windows converting application dBpoweramp under wine I set it to convert the copy of my library residing on my backup drive. I planned to keep both lossless and lossy versions stored on the backup and then keep only the lossy version on the laptop's internal drive. Once the conversion was complete I deleted the copy of my library on the laptop to make room for the new one. 

On a whim I also decided to clear some space on my desk by moving the external drive off of it. I tried to unmount it but a message appeared saying there were still some processes running and the drive was in use. Some dBpoweramp-related processes were still running it turns out, even though the conversion had finished several minutes ago. I killed all the processes (which apparently was a bad move) and then unmounted the external drive and powered it off. Once I plugged it back in and attempted to mount it I got the following error:

```
Error mounting: mount exited with exit code 11: ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory

ntfs-3g 2011.4.12AR.4 external FUSE 28 - Third Generation NTFS Driver
		Configuration type 7, XATTRS are on, POSIX ACLS are on

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2011 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

News, support and information:  http://tuxera.com
```


Now since I hadn't yet re-copied my library back to my laptop's internal drive, my library is stuck on the external drive and I can't access it. There is still an unconverted copy saved on my mp3 player's drive so all is not completely lost, but it took almost 48 continuous hours to convert, with lots of bugs and annoyances along the way, and I sincerely hope I don't have to go through that again. Please help!

---

### Post by hitchhiker4242 on 2011-11-30
Nevermind. After rebooting this problem went away. Sorry for posting so hastily and crowding up the forums. I was freaking out! :roll:

---

### Post by nothingspecial on 2011-11-30
Don't worry about it :)

---

