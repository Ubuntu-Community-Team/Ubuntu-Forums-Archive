---
title: "RSync - Cannot delete non-empty directory."
date: 2009-09-23
forum: General Help
---

### Post by Roasted on 2009-09-23
Why am I getting this error?

jason@Area51:~$ backup
sending incremental file list
rsync: opendir "/media/localbackup/.Trash-1000/expunged/711697344/2009-09-23_00.28.08.341112.Area51.ful" failed: Permission denied (13)
cannot delete non-empty directory: .Trash-1000/expunged/711697344/2009-09-23_00.28.08.341112.Area51.ful



backup script:

#!/bin/bash
rsync -a --progress --delete /home/jason/ /media/localbackup/

---

### Post by tkoco on 2009-09-23
Most likely the destination directory permissions won't let you. Who owns the "/media/localbackup" directory? What sort of filesystem is "/media/localbackup" formatted to? Ext3? VFAT? NTFS? Each respective filesystem has it's quirks.
> **Roasted said:**
> Why am I getting this error?

jason@Area51:~$ backup
sending incremental file list
rsync: opendir "/media/localbackup/.Trash-1000/expunged/711697344/2009-09-23_00.28.08.341112.Area51.ful" failed: Permission denied (13)
cannot delete non-empty directory: .Trash-1000/expunged/711697344/2009-09-23_00.28.08.341112.Area51.ful



backup script:

#!/bin/bash
rsync -a --progress --delete /home/jason/ /media/localbackup/

---

### Post by Roasted on 2009-09-23
drwxr-xr-x 80 jason jason      4096 2009-09-23 21:16 localbackup


EXT3

It worked fine before. I have no idea what's up with it now. I've had this setup since Jaunty came out.

---

### Post by Roasted on 2009-09-24
Fixed.

Somehow a directory named .Trash-1000 was created on /media/localbackup, but it didn't exist on my home directory. That's something I didn't get, but whatever. I just used terminal and navigated to /media/localbackup and ran

sudo rm -r .Trash-1000

re-ran my backup script and it worked without error.

Again, no idea how it happened. And I was even the owner of .Trash-1000 on /media/localbackup, so I'm not sure why the --delete tag in my rsync script didn't delete it, since it wasn't on home. Said something about permission denied (but again, I owned the damn thing). But that's what I did to get it working again.

---

### Post by tkoco on 2009-09-24
Congratulations! Glad to hear that you got that one solved. Sometimes one can not see the forest because the trees are in the way.
> **Roasted said:**
> Fixed.

Somehow a directory named .Trash-1000 was created on /media/localbackup, but it didn't exist on my home directory. That's something I didn't get, but whatever. I just used terminal and navigated to /media/localbackup and ran

sudo rm -r .Trash-1000

re-ran my backup script and it worked without error.

Again, no idea how it happened. And I was even the owner of .Trash-1000 on /media/localbackup, so I'm not sure why the --delete tag in my rsync script didn't delete it, since it wasn't on home. Said something about permission denied (but again, I owned the damn thing). But that's what I did to get it working again.

---

### Post by Roasted on 2009-09-25
> **tkoco said:**
> Congratulations! Glad to hear that you got that one solved. Sometimes one can not see the forest because the trees are in the way.

Yeah, but it's like anything else though - think slow and logically and it's amazing what you can figure out. I used to be very impatient with this stuff and go nuts, therefore leaving me with a 3 week long problem, instead of a 4 minute problem.

---

