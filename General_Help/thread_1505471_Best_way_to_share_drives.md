---
title: "Best way to share drives"
date: 2010-06-09
forum: General Help
---

### Post by Jake007g on 2010-06-09
Well to start with, I have an Ubuntu 10.04 Lucid Lynx laptop, and an Ubuntu Studio 10.04 Lucid Lynx desktop. 

My desktop has a 400gb internal hard disk, and a 1tb external hard drive. 

What is the easiest, and most reliable way to access the files on my external hard drive on my Laptop via my wireless network (can't plug it in directly)? 

Thanks a lot in advance

-Jake

---

### Post by lizzard on 2010-06-09
If both computers are connected via a local network, NFS would be a reliable possibility.
Check out: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by Jake007g on 2010-06-09
Thank you, I'll check that out right away :-)

---

### Post by John Bean on 2010-06-09
It's not clear from your question whether you are in a position to physically access the external hard disk with your laptop. If so, just plug it in...

If you mean over a network with the disk still connected to the desktop machine then I'd second the suggestion of using NFS if you want transparent access.

---

