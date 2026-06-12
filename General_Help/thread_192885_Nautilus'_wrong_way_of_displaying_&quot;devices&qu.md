---
title: "Nautilus' wrong way of displaying &quot;devices&quot;"
date: 2006-06-09
forum: General Help
---

### Post by deb2006 on 2006-06-09
Right now Nautilus displays various partitions _and_ a root filesystem. This, in my eyes, is wrong. There should only be one entry called "Filesystem" since e.g. boot, home etc. are located under /. Why was the view we get with Dapper introduced? It's truly awful and doesn't have anything to do with the UNIX way of dealing with a filesystem. Too bad :(((

Either Nautilus displays devices. Ok, then I'd have two hard disks with various partitions. Or Nautilus does it the UNIX way and has ONE root filesystem which has various mountpoints for all kinds of devices.

---

### Post by lkagan on 2006-06-09
It's not that big of a deal to me since I rarely see that view anyway.  But let's think about this for a second.  If we go the traditional UNIX way, then all we would ever see is the root filesystem.  CDROM's, Floppy's USB drives, and network mounts would all be under this mount point.  

What Ubuntu has done is decided to show  all mount points.  I think this is overkill.  I personally would have gone with a system where we display the root filesystem, then any external filesystems such as external drives and network shares.  I don't see the need to display /var, /home, /boot, etc... in the 'Computer' view.

But these engineers have had countless hours of arguments over choices like this.  I believe it's inline with their strategy.  It appears they are targeting this distro to office environments.  This is made apparent by the certifcation that will be available later this quarter where 20% of the exam will cover the Gnome desktop and applications.

Larry

---

