---
title: "Karmic still says HardDrive is failing"
date: 2009-11-03
forum: General Help
---

### Post by YosefKaro on 2009-11-03
I just switched from wubi to a fresh install yesterday.  I was thinking that this was a bug in wubi that I could safely ignore.  However, Karmic is still reporting that my HD may be failing even after doing a fresh install.  I don't get it though: I ran a bunch of tests from Windows on my HardDrive and they all reported that my HD is healthy; only Karmic says that it is unhealthy (very unhealthy with 82 bad sectors).  I don't want to have to spend money that I don't have unless I don't have any other choice: How can I run a really reliable test on my harddrive...is there some really good application out there that I can download to get a 'second opinion' on this ?  Any suggestions are welcome.  Thank you.

-Yos

---

### Post by fanglinyong on 2009-11-03
you can use some software to fix your bad sectors! and if ti can't fix your bad sectors, it can hide your bad sectors!so ,after doing this, you will found that you can install ubuntu in your HD!

---

### Post by djodjoman on 2009-11-03
Wich software?

---

### Post by P4man on 2009-11-03
You can not fix bad sectors. You can at most make a filesystem avoid bad sectors, but this is not what the OP needs.

YosefKaro, you need a [smart monitoring tool]("http://en.wikipedia.org/wiki/Comparison_of_S.M.A.R.T._tools") to confirm (or contradict) palimpsest's warning. 

edit: use this 
[http://www.almico.com/speedfan439.exe](http://www.almico.com/speedfan439.exe)
in windows. Go to SMART and post what it reports.

---

### Post by YosefKaro on 2009-11-03
Thank you p4man...now it is confirmed that my HD is dying :(  At least I know ahead of time thanks to Karmic; I wouldn't have found out about this ahead of time otherwise.

-Yos

---

### Post by P4man on 2009-11-03
Im not surprised Im afraid. The palimpsest bug seems to report either negative or extremely high values. If you get either, then you can ignore the warning but 82 sounds perfectly credible and I have yet to see anyone confirm such a value is indeed caused by a bug in palimpsest. 

Sucks for you, but indeed its better to know beforehand.

---

### Post by nerdy_kid on 2009-11-03
your HDD might not be bad -- check this out:

[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/438136)


I get the same issue, along with a ton of other people (as u can see)


I would get disk-checking software from the disks manufacturer before u buy!

---

### Post by P4man on 2009-11-03
> **nerdy_kid said:**
> your HDD might not be bad -- check this out:

[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/438136)


I get the same issue, along with a ton of other people (as u can see)


I would get disk-checking software from the disks manufacturer before u buy!

He knows that. But another smart monitoring utility under another OS confirmed his dying harddisk, **not every warning of palimpsest is incorrect**! in fact, **only** the obvious wrong results (negative bad sector count or extreme high counts) seem incorrect.

---

### Post by nerdy_kid on 2009-11-03
sry somehow missed that post...

---

### Post by bpeyser on 2009-11-03
@P4man:
> He knows that. But another smart monitoring utility under another OS confirmed his dying harddisk, **not every warning of palimpsest is incorrect**! in fact, **only** the obvious wrong results (negative bad sector count or extreme high counts) seem incorrect. 	

I don't think this is fully correct.
[http://ubuntuforums.org/showthread.php?t=1305452&page=3](http://ubuntuforums.org/showthread.php?t=1305452&page=3)
In some cases, palimpsest gives you good info, so you're right that not every warning is bogus. If the numbers are crazy, it's certainly a bug causing it, but even if they're reasonable the warnings could be incorrect.

I think he should double-check with a manufacturer-supplied utility before replacing the drive. And make sure his data is backed up as if the drive is about to fail, every day.

-bpeyser

---

