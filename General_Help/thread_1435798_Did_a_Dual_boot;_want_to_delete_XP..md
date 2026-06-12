---
title: "Did a Dual boot; want to delete XP."
date: 2010-03-21
forum: General Help
---

### Post by JakeIsWIn on 2010-03-21
I decided to re-try Ubuntu (9.10), so I made a dual-boot from Windows XP professional. But now I'm running out of space, and I've seen how god-awful Windows is compared to Ubunutu. But I don't really know how to go about this... Any advice or links to guides  would be appreciated!

---

### Post by dcstar on 2010-03-21
> **JakeIsWIn said:**
> I decided to re-try Ubuntu (9.10), so I made a dual-boot from Windows XP professional. But now I'm running out of space, and I've seen how god-awful Windows is compared to Ubunutu. But I don't really know how to go about this... Any advice or links to guides  would be appreciated!

You can use the Partition Manager to simply delete the Windows partition, but you then *may* have to reinstall Grub.

Just search out the grub reinstall instructions and have them handy just in case.

---

### Post by JakeIsWIn on 2010-03-21
Ehhh, how would I go about navigation to the partition manager?

---

### Post by Megafag on 2010-03-21
> **JakeIsWIn said:**
> Ehhh, how would I go about navigation to the partition manager?

from terminal:

```
sudo gparted
```

---

### Post by JakeIsWIn on 2010-03-21
Ahhh, thanks.

---

### Post by JakeIsWIn on 2010-03-21
Snip

---

### Post by Megafag on 2010-03-21
> **JakeIsWIn said:**
> Snip

Wut?

also if this resloved your problem you might wanna mark the thread "resolved".

---

### Post by raymondh on 2010-03-21
> **JakeIsWIn said:**
> I got: jake@JakeIsWin:~$ sudo gparted
[sudo] password for jake: 
sudo: gparted: command not found

Better use gparted from a liveCD.  That will unmount any partition you want to delete.

-  boot into liveCD
-  Go live session (try ubuntu without changes)
-  in live session, access gparted (system > administration)
-  in gparted, 2-check that the partition you want to delete is unmounted by right clicking said partition and if given the option to unmount, do so.  For swap, select swapoff.

Also, to be on the safe side ... have a working/tested back-up of your files (windows and ubuntu) .... in case you accidentally delete the ubuntu partition.

---

### Post by Megafag on 2010-03-21
> **raymondh said:**
> Better use gparted from a liveCD.  That will unmount any partition you want to delete.

-  boot into liveCD
-  Go live session (try ubuntu without changes)
-  in live session, access gparted (system > administration)
-  in gparted, 2-check that the partition you want to delete is unmounted by right clicking said partition and if given the option to unmount, do so.  For swap, select swapoff.

Also, to be on the safe side ... have a working/tested back-up of your files (windows and ubuntu) .... in case you accidentally delete the ubuntu partition.

The ubuntu live CD/DVD generally comes with gparted, so you can use that.

---

### Post by JakeIsWIn on 2010-03-21
> **Megafag said:**
> The ubuntu live CD/DVD generally comes with gparted, so you can use that.


I misplaced that CD, I last had it about a year ago anyways. Im currently burning GParted to a disk.

---

