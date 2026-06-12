---
title: "Sudden GRUB Error 25"
date: 2010-07-20
forum: General Help
---

### Post by dpm_edinburgh on 2010-07-20
I started my laptop this morning with no problems.  It was doing a file system check which I quit (pressing C) after about 30%.  The only problem I had was wired networking didn't seem to be working (though wireless was).  No problem: this happens sometimes and a restart fixes it.

After restart: the GRUB screen hangs at "Loading stage 1.5" for ages before issuing Error 25.  Um, try a restart.  Same thing.  And again.

Any idea what's happened?  I'm on Lucid 10.4, no other OS installed, Toshiba laptop that up to now has had no problems with the last two versions of Ubuntu.

Thanks for any help.

---

### Post by rubylaser on 2010-07-20
An Error 25 is a  Disk read error.  This error is returned if there is a disk read error when trying to probe or read data from a particular disk.  You may have experienced a hard drive failing.  I'd

```
apt-get install smartmontools
```
And then run a hard drive test and see if it can pass a smart test.

If it failed, I'd throw in the livecd, and use gddrescue to recover my files to an external drive.

---

