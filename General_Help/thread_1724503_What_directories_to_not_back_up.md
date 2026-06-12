---
title: "What directories to *not* back up?"
date: 2011-04-08
forum: General Help
---

### Post by Fraoch on 2011-04-08
I back up using a small rsync script.  I've tried other methods but just keep coming back to it.

I have enough space that I can back up the entire root file system, but for speed and economy there are certain folders I'm not backing up.  I understand some are dynamically generated on boot, others are caches.

/proc
/lost+found
/mnt
/sys
/home/[me]/.mozilla/firefox/izy7ta6b.default/Cache (Firefox cache)

Anything else I should exclude?  How about APT's cache?  /var?  Any other caches?

---

### Post by 3Miro on 2011-04-08
When I do this kind of backup, I boot from a LiveCD and then backup everything. That way proc and dev are empty, but if I copy them on a new partition and boot, then they will be there to be populated. You don't want to boot without an empty /proc and /dev.

---

### Post by Telengard C64 on 2011-04-08
[list]
[*]**/dev** is probably not necessary to backup
[*]**/media** is usually only external storage devices, so you probably want to skip it
[*]**/tmp** is automatically deleted on reboot anyway
[/list]

**_Edit_**
You may want to selectively keep parts of **/var**, especially if you run (for example) apache.

[more discussion](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by Fraoch on 2011-04-08
Thanks for the responses so far.  It seems I'm having a hard time rsync'ing /proc anyway, there's something odd about this folder - Nautilus shows it as being 128 TB (!) in size.  rsync wants to take ~640 hours to sync it.:lolflag:

I'll manually place an empty /proc and /dev in the backup folder then.

---

