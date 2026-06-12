---
title: "symbol not found 'grub_putchar' &amp; grub rescue prompt"
date: 2011-12-04
forum: General Help
---

### Post by jamesisin on 2011-12-04
I have a machine with three partitions containing Ubu, Win7, and WinXP.

The installation of Win7 confused grub (someone else did the 7 install after I had built the machine with the other two working).  I thought I'd just re-install Ubu 10.04 and grub and that would solve the matter.

Unfortunately now that I have re-installed Ubu and grub I get a grub rescue prompt with the error message "error: symbol not found: 'grub_putchar'."

Next steps?

---

### Post by jamesisin on 2011-12-05
Anybody?

---

### Post by jamesisin on 2011-12-14
I could really use a little help with this one.

---

### Post by jamesisin on 2011-12-15
Any grub experts awake?

---

### Post by seawolf167 on 2011-12-15
Follow [this guide]("http://ubuntuforums.org/showthread.php?t=1581099") to purge and reinstall Grub2. Once you have done that and have booted back into Ubuntu, run this command to pick up the other partition boot loaders

```
sudo update-grub
```

then restart and ensure you can access the other installations.

---

### Post by jamesisin on 2011-12-18
Didn't I already re-install grub when I re-installed 10.04?  I instructed the installer to install a boot loader.  What else would have been needed?

---

### Post by seawolf167 on 2011-12-18
> **jamesisin said:**
> Didn't I already re-install grub when I re-installed 10.04?  I instructed the installer to install a boot loader.  What else would have been needed?

Yes, but there are things that carry over from the initial installation to the new installation (of Grub) which is why a purge and reinstall is necessary.

---

### Post by jamesisin on 2011-12-20
Thanks for pointing to those instructions.  Without them I would have struggled along under the delusion that I understood the problem to be a simple grub issue.  Turns out it was little related to grub and thus more complex.  Please allow me to bring you up to speed and so you might help with this one last piece of the puzzle.

When I built the machine in question it contained three drives we will call A, B, and C.  A and C were 150 GB drives and A contained XP while C contained Ubuntu.  B is 1.5 TB for storage and contained only backups of both the other drives.  This was all working as expected when I sent it to the client.

Subsequently the video card went bad and in testing that problem the other IT person (yes, they actually touched my machine!) made the following changes for whatever reason.  Drives A and C were seemingly unchanged but drive B was formatted (bye-bye backups) and installed with Windows 7.  I am told Windows 7 would boot but I never saw that in action.  The other two operating systems would not boot due to the problem which prompted this thread.

Turns out the problem looks to be a physical drive problem.  When I followed the grub instructions you linked I encountered several IO errors in attempting to access drive C.  So I shifted the partitions around and rebuilt Ubuntu on drive A along side XP.  Further I included partition/space for 7 and subsequently copied (using dd) the two Win7 partitions from B to A.  Finally I ran update-grub and grub picked up all of the operating systems (XP, Ubu, and both 7's).  (I have disconnected drive C.)

Booting brings me to the grub menu for selecting where to boot.  XP and Ubu boot as expected.  Neither of the 7 partitions boot; they each hang as a flashing cursor indefinitely.  I can mount all of the partitions from Ubu so I ought to be able to make any file-level changes which might be required, and I'm hoping kick-starting 7 will be something simple at this point.

Is it?

---

### Post by jamesisin on 2012-01-03
New thread for this last part of the problem:

[http://ubuntuforums.org/showthread.php?p=11584551](http://ubuntuforums.org/showthread.php?p=11584551)

---

