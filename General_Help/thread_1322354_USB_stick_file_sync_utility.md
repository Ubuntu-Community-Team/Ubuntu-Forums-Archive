---
title: "USB stick file sync utility"
date: 2009-11-10
forum: General Help
---

### Post by mwalimu54 on 2009-11-10
I am looking for a gui based utility that will automatically sync the contents of my usb stick with the contents of certain folders on my HD.  The app would be something similar to Dropbox except the "cloud" would be on my usb stick rather than on a server.  I would just use Dropbox (which I love) except that my one machine has no internet access and no possibility of getting it.  The app would also need to be **cross-platform between XP and Ubuntu.**

In other words, I have an XP box _without_ internet access at work and an Ubuntu box _with_ internet access at home and would like to shuffle a USB stick back and forth to keep my files synced between the two machines.

I would want the newer version of any updated file to overwrite the older one.

Any suggestions?

---

### Post by Giblet5 on 2009-11-10
Winzip and Winrar can both read compressed tar archives.

Example use:

On linux: ```
tar -czf /media/Cruzer/sync.tar.gz Music Documents Downloads/*.torrent
```

On XP: Just open the archive with Winzip or Winrar and extract what you need.

---

