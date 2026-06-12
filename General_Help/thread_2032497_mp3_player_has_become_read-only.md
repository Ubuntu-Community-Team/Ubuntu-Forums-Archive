---
title: "mp3 player has become read-only"
date: 2012-07-24
forum: General Help
---

### Post by NautiusMaximus on 2012-07-24
I have a little script which uses rsync, which I use to copy podcasts onto my mp3 player. This has been working without any trouble for many months.

However, this week, it has failed. It tells me that my mp3 player has a "read only file system". If I try manually to delete files from my mp3 player or add new ones to it, either from the desktop GUI or at the terminal, I get the same error. This is true even using sudo rm or sudo cp at the terminal.

Any idea what could be causing this and how I could fix it? I haven't made any changes to my system lately other than the regular system updates via the update manager.

Many thanks
NM

---

### Post by dcstar on 2012-07-24
> **NautiusMaximus said:**
> 
........
However, this week, it has failed. It tells me that my mp3 player has a "read only file system".
........
Any idea what could be causing this and how I could fix it? I haven't made any changes to my system lately other than the regular system updates via the update manager.


You have probably uncleanly disconnected the device. Use the Disk Manager or gparted to do a filesystem check on the device.

---

### Post by NautiusMaximus on 2012-07-24
Brilliant, thanks, that seems to have done the trick. I did a file system check with Disk Utility. It didn't report any problems, but maybe it just silently fixed them while it did the check, because everything worked just fine after that.:)

---

