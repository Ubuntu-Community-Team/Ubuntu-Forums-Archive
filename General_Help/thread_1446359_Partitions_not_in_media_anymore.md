---
title: "Partitions not in /media anymore"
date: 2010-04-03
forum: General Help
---

### Post by chipchop on 2010-04-03
Long story short:
I was trying to make a wow server, never did get it to connect, screwed up the smb share to my xbmc, removed everything called mysql and samba through the package manager.  
All that other stuff I can hammer through, but after my last reboot - none of my partitions are showing up in the /media folder - therefore I cannot mount them.  I reinstalled samba, no change.  They are all listed in gparted and all have uuid's and labels list for blkid - what the heck did i do, and should I just fresh install the koala?


I was able to mount the partitions through the Palimpsest Disk Utility, haven't rebooted yet, so hopefully it stays. If not then maybe a reply will help me fix what i messed up

---

### Post by gzarkadas on 2010-04-04
What are the contents of your /etc/fstab? Maybe the partitions you used to see in /media are referenced there? Have you used Log Viewer to browse your syslog for errors during the last boot (and just before) giving a hint for the cause of this behavior?

---

### Post by Morbius1 on 2010-04-04
Why not post the output of some of the things you mentioned:

**sudo blkid -c /dev/null**
**cat /etc/fstab**
**mount**

Not sure what samba and mysql has to do with all this. Make sure you run the blkid I mentioned above. It resets the cache and gives you an accurate output.

---

### Post by chipchop on 2010-04-04
The partitions are not references in the fstab. Syslog does not appear to reference an error regarding the uuids. I have been manually adding some packages.  Surely I am just mucking the whole thing up with things I don't need.  The term, "know enough to be dangerous" suits this situation quite well.  I certainly lost some crucial files when I removed samba and mysql.

---

### Post by gzarkadas on 2010-04-04
From a terminal window issue `sudo mount' and copy (with `Ctrl+Shift+C') the output and post it here. Also the uuids of the media that you cannot see in /media. This may give us a clue.

In addition, verify that:

[LIST=1]
[*]you do not by accident mount something in /etc/fstab as /media
[*]your account privileges include `Mount user space filesystems (FUSE)' (go to System|Administration|Users and Groups|User Rights tab)
[/LIST]

---

### Post by chipchop on 2010-04-07
Thanks for the answers, so wierd.  I was able to mount the drives in terminal, and set it up to mount automatically upon boot.  It was just strange to me that removing packages associated with samba and mysql would have reacted with the partitions in such a manner.  My karmic32 file structure was terribly unkempt, so I decided to make a fresh karmic64 install and use that one.  That's one way to skin a cat, I suppose.  Ctrl+Shift+C, man that is so much better than using the menu bar to copy and paste. Sorry I was so quick to give up this, I really don't anticipate anyone else having this issue.

---

