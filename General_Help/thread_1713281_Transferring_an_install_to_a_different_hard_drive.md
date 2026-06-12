---
title: "Transferring an install to a different hard drive?"
date: 2011-03-23
forum: General Help
---

### Post by Dustin2128 on 2011-03-23
The HDD in my HTPC is giving off a really annoying grinding sound, and we all know what that means. Luckily, my movies, songs, games, etc. are stored on a brand new 400 Gig external drive- the install is all that's on the failing one. I've got about a half dozen IDE drives big enough for a base install, and at least half of those *aren't* failing, I just don't know what to do. Do I just create the ext and swap partitions then copy/paste the file system, or what?

---

### Post by PCNetSpec on 2011-03-23
There is technically nothing stopping you doing that, ie. copy EVERYTHING, but then you'd have to boot from a LiveCD, chroot, and reinstall the GRUB bootloader to the new drive.

Easiest way... just clone the drive with something like a Clonzilla LiveCD:

[http://clonezilla.org/clonezilla-live.php](http://clonezilla.org/clonezilla-live.php)

Or Clonezilla from another "Disk tools" type LiveCD, such as Parted Magic:

[http://partedmagic.com/doku.php?id=start](http://partedmagic.com/doku.php?id=start)

Or if you fancy getting dirty on the command line, you could use dd

---

