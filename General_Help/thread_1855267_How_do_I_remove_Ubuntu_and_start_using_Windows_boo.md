---
title: "How do I remove Ubuntu and start using Windows boot manager again?"
date: 2011-10-05
forum: General Help
---

### Post by josephellengar on 2011-10-05
Hi there. I installed Ubuntu on a friend's PC and she doesn't like it. She'd prefer to continue using W7. Unfortunately, I have never taken Linux off a computer before. Is there a way to remove Ubuntu and grub from a hard disk and then go back to using the normal Windows boot manager? How would I do this?

---

### Post by 3Miro on 2011-10-05
How did you install Ubuntu. If you used Wubi, then you can go to Add/Remove Programs and remove Ubuntu.

If you installed it on its own partition, you need to go into Windows and look for a way to repair the Windows bootloader. Once you have repaired the bootleader, you can delete the Linux partition. You may need a Windows 7 CD for that, but I am not sure about it.

It is important to not delete the partition until AFTER you have restored the Windows bootloader, otherwise you will not be able to boot the machine.

---

### Post by fantab on 2011-10-05
If you already have a backup Windows then **just delete the UBUNTU partition(s) or Format them, Restart the PC and you will have Windows7 booting.**

If you don't have windows backup then get one. If you don't mind reinstalling windows again, then I suggest it will be better to do so. But just make sure you have backed up your important data.

---

### Post by bcbc on 2011-10-06
First create a windows repair CD if you don't have one already - you can create it right from Windows 7 with a blank CD-R (assuming it has a CD-RW drive).

Then boot using the CD to a repair prompt and install the windows bootloader:
```
bootrec /fixmbr
```

Make sure the computer boots straight into windows. Then use the 'disk management' to delete the ubuntu partition and you can then merge it with an existing windows partition or leave it separate.

If you installed with wubi, as mentioned, just use control panel to uninstall. No further messing about required.

Note, as *3Miro* also stated, you **must** replace the windows bootloader before removing the ubuntu partition or nothing will boot.

---

### Post by josephellengar on 2011-10-06
Thanks! Fixed my problem.

---

