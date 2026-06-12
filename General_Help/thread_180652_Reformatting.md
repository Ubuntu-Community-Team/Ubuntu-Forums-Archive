---
title: "Reformatting"
date: 2006-05-22
forum: General Help
---

### Post by LinuX Nova on 2006-05-22
Hey, I want to reformat my hard drive to the format supported by Windows 98 and above, Fat32 is it not? I'm guessing I go into recovery mode? Then what?

Thanks,

LXN

---

### Post by christhemonkey on 2006-05-22
I think you might need a live disc/install cd.

To reformat a drive, it has to not be mounted.
(ie like you do with a live cd)

Then you need to type
```
sudo mkfs -t vfat /dev/hda1 
```
Or something along those lines.


But please be aware that you will lose everything on that disk, so back up what you want to keep!

---

### Post by LinuX Nova on 2006-05-22
Thank you.

---

