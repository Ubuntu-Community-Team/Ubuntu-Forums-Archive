---
title: "Lost all my jpg"
date: 2009-09-09
forum: General Help
---

### Post by bonicideur on 2009-09-09
Ok, I am desperete:

I have a dual boot ubuntu/xp, for six month now...I have two harddrive c et d
XP and ubuntu are installed on c...and d is ntfs formated, and I use d: as my data folder for the two OS...
But, yesterday after putting XP to hibernate and booting in ubuntu, I've decided to "just" watch my personal photos with digikam....
After that, I've puted ubuntu to hibernate and booted xp again......Big surprise..impossible to access the folder of my photos...So I've shut down XP and booted back to linux....and inside the photos folder there is Nothing...

SOMEONE PLEASE HELP...all my photos

---

### Post by Essary on 2009-09-09
is it the entire drive or is it just your jpgs?

---

### Post by earthpigg on 2009-09-09
```
sudo apt-get install testdisk
```

```
sudo photorec
```

ensure you read what is on the screen in photorec, and make a new folder (not on what you are calling the "D" drive) for the recovered photos to go to.

---

### Post by bonicideur on 2009-09-09
OMG, thank you that worked....all my photos are in a folder on my /home....  But wat was the reason of this...how to avoid it in the future this kind of problems?  Thank you both for your help.

---

### Post by AliTabuger7 on 2009-09-09
Is there a chance that the application you were using in ubuntu tried to consolidate your photo library?

---

### Post by earthpigg on 2009-09-09
glad it worked :D i make spare change on the side using photorec.

[http://sfbay.craigslist.org/nby/pho/1366544199.html](http://sfbay.craigslist.org/nby/pho/1366544199.html)

> **bonicideur said:**
> OMG, thank you that worked....all my photos are in a folder on my /home....  But wat was the reason of this...how to avoid it in the future this kind of problems?  Thank you both for your help.

i really don't know.

you said you had both Windows *and* Ubuntu on your "C Drive"?

i know i am _**very**_ skeptical of wubi installs, but i can't specifically place the blame there without further/exact knowledge of how your system is configured and what you where doing and what you had installed, etc...

the old saying may or may not apply in this case:

*if the bug cannot be reproduced, it is not a bug. it is either user error or hardware failure.*



in this case, it could *also* be NTFS failure. NTFS failures can be reproduced, but that is a windows problem and not an ubuntu one.

so there you have it, four possibilities:
1. bug. we would need to be able to reliably reproduce your problem on demand for this to be the case.
2. user error.
3. hardware failure. keep your eyes keen for future things like this. in fact, it couldn't hurt to run badblocks, fsck, and scandisk (for the NTFS partition) on that machine.
4. Windows/NTFS failure or bug. see #1 about being able to reproduce the issue.

---

### Post by earthpigg on 2009-09-09
and also: you back up your important data on another physical hard drive, right?

**_right?_**

---

