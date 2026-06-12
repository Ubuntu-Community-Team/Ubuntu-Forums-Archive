---
title: "Ubuntu hard drive recovery"
date: 2009-11-25
forum: General Help
---

### Post by Methuselah on 2009-11-25
Sometime ago I suffered a system hang with Ubuntu Hardy Heron which necessitated hard rebooting my system.
It failed to come up successfully on reboot but I was able run fsck and mount the HDD from a Live CD.
Since the system still fails to boot my plan was to rescue my data and just start over.

However, I noticed tthat when browsing the HDD from the LiveCD, some of the files have an emblem (an orange square with lines trough both diagonals forming a cross) on some files and they refuse to open or be copied.
Some folders including Lost+Found have this emblem and cannot be browsed since they give a permission error.
Some files in my home folder show this but some files do not; it seems arbitrary.

So my question is whether this is really a permission error or these files are simply corrupted beyond repair.
Do you think I could possibly open these files if I could boot the hard drive and log in?
If so, how could I recover the contents of the boot or system area without reinstalling the whole OS and losing the salvageable data?

What I really want to know is whether the files that I can't read can be saved and if so how?
I'm not sure whether they are corrupted or it is a permission issue as the error message suggests.
Though I can't understand why some of my files would be locked and others not.

I'd really appreciate any pointers.
Thanks.

---

### Post by cariboo on 2009-11-25
It may well be a permissions error. You have to be root in order to access lost+found. When running the Live Cd press Alt-F2 and type:

```
gksudo nautilus
```

This will allow you to run the file manager as root and you can access lost+found as well as any other files/directories that need root to access them.

---

### Post by Methuselah on 2009-11-25
> **cariboo907 said:**
> It may well be a permissions error. You have to be root in order to access lost+found. When running the Live Cd press Alt-F2 and type:

```
gksudo nautilus
```

This will allow you to run the file manager as root and you can access lost+found as well as any other files/directories that need root to access them.

Thank you very much cariboo907!
I'll give that a try.

---

### Post by Methuselah on 2009-11-25
Thanks, that worked!

I have one more question for you:

Is there any kind of minimal ubuntu re-install that will get the system booting again without overwriting data in home?

I used the default partitioning scheme when installing Ubuntu.

---

