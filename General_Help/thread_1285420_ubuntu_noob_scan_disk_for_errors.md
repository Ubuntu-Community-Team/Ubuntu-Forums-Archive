---
title: "ubuntu noob: scan disk for errors?"
date: 2009-10-07
forum: General Help
---

### Post by osomphane on 2009-10-07
I'm sort of a newbie and my netbook fell from the table on a carpet floor. Didn't hear a scratching noise, but don't know if the drive was reading at that time or not.

Anyway, I ran an fsck check on my partitions and it didn't say there were errors but it didn't say there were zero bad sectors either. So, could anyone help me with the following questions:

Will fsck scan free space for hardware damage?
Will it tell me if there is a physical problem or detect bad sectors?
When I install Ubuntu 9.10 at the end of the month (clean install), will it scan the hard drive for problems before installing?

I don't hear any noise from the hard disk, but paranoia keeps me awake at night, so I'd thought I'd ask here :)

---

### Post by jeremyswalker on 2009-10-07
fsck just checks the file system, not the physical health of the hard drive.

You may want to look into the program 'hdparm'. That may be more of what you are looking for. Be careful though. Type 'man hdparm' for all the options.

---

