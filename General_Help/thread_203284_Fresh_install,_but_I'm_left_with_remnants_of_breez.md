---
title: "Fresh install, but I'm left with remnants of breezy"
date: 2006-06-25
forum: General Help
---

### Post by timsch75 on 2006-06-25
I just made a fresh install of Dapper.  I still have some icons (which don't work) from my Breezy install.  I intended it to format the partition.  Could I still have these icons if it actually formatted it?

---

### Post by aysiu on 2006-06-25
How is that possible? A fresh install overwrites a previous install.

You did mean an *install* and not an *upgrade*, right?

---

### Post by timsch75 on 2006-06-25
Yes, I meant install.  I installed with the graphical CD at which time I deleted the partition and recreated it, formatting it with the same file structure, ReiserFS.  My screen resolution was generic and I thought I could get past this by installing with the alternate CD (wrong, but that's another issue).  I instructed this installation to format the partition as well.  After all of this, I still have icons, bookmarks, etc.  However, installations like Fluxbox are gone.  I'm baffled

---

### Post by incubus on 2006-06-25
Oh wait, but you have your /home in a different partition, right?

If that's the case, you just need to move/remove some hidden directories there. We'd need to know which ones you want purged.

If that's not the case, looks like the installer is not really formatting your partition. We could try doing it manually.

incubus

---

### Post by timsch75 on 2006-06-25
Of course....  I never thought of the /home directory being the reason.  It is on its own partition.  I'll look through it to see what may be purged, but that's probably not necessary.  Thanks, Inc.

---

### Post by incubus on 2006-06-25
No problem!
Remember you can just move some directories in case you want a backup.

Say you have firefox:
```

$ cd
$ mv .mozilla/ .mozilla.bak/

```

I'm not familiar with Gnome, but for KDE you'd do ~/.kde .

incubus

---

