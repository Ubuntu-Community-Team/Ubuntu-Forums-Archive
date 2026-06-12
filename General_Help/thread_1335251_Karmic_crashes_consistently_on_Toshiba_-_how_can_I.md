---
title: "Karmic crashes consistently on Toshiba - how can I report it?"
date: 2009-11-23
forum: General Help
---

### Post by FunkeyMonk on 2009-11-23
Ubuntu Karmic Koala 9.10 kernel 2.6.31-15-generic crashes consistently on my Toshiba Satellite M115-S1061.  

It boots fine, and I got wireless working thanks to some backports.  But the system crashes HARD every single time I boot it.  It'll run for about 2-3 minutes perfectly well, and then completely freeze.  I can't force quit anything, the mouse is frozen, and keyboard shortcuts don't work.

Is there a way I can find some sort of crash report and send it in?  Is there a log file somewhere that might be capturing this crash every time?

FWIW, I do NOT have this problem if I boot into the older 2.6.28-16-generic kernel.

---

### Post by FunkeyMonk on 2009-11-29
Updated, but not resolved:

I just installed the Xorg update through Update Manager.   I'm guessing the problem is with Xorg's handling of my USB devices.  (Xorg does handle USB, doesn't it?)  After the update, Karmic now stays fully operational (and wonderful) for about 10-15 minutes -- much longer than before.  

But it still crashes hard.   I believe it's a USB problem, because now my USB keyboard and mouse stop working, but the laptop's trackpad and built-in keyboard continue to work normally for a brief time before the whole thing crashes hard.

Again-- is there an xorg log file somewhere that I could send as a bug report?

---

### Post by FunkeyMonk on 2009-11-29
As suggested elsewhere, I have turned off proposed updates, and reverted to the -14 generic kernel (as opposed to the -15).   I still have the crashes.

---

### Post by jukzh on 2009-12-13
Toshiba L20 today has been crashed two times, first with symptoms as described above
and just now with dead black console.

Linux toshiba 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux 
9.10 (karmic)
Gnome 2.28.1
Memory: 488 Mib
Intel(R) 1.73GHz

---

