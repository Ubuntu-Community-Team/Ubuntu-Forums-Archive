---
title: "Xubuntu install -- &quot;disk read error&quot; when booting to XP"
date: 2012-07-14
forum: General Help
---

### Post by lykwydchykyn on 2012-07-14
Quick story:  Neighbor kid bought a used computer, and wanted me to install Linux dual-boot with XP (mostly at my son's urging).

Things seemed to work fine off the liveCD, so we resized the NTFS partition down by 10 GB (it's a 72 GB partition, tons of free space) and installed Xubuntu.

After it finished, we rebooted, and the mouse and keyboard didn't work in Xubuntu.  So we tried to boot back into Windows XP, and it won't boot.  After selecting it, we just get:

```

A disk read error has occurred.  Press Ctrl-Alt-Delete to restart your computer

```

The windows partition is still there, still has all its files, I can mount it from a LiveUSB easily.

So far I've tried:

 - chkdsk /r from recovery console
 - fixmbr
 - fixboot
 - reinstalling grub

Nothing works; XP just won't boot.  Right now I'm doing a system restore from the recovery partition (thankfully runnable from grub), but I don't know if that will work.

Has anyone seen this issue, and can anyone help me fix it?

---

### Post by ajgreeny on 2012-07-14
How did you shrink the XP partition?

If you moved the whole partition to the right in order to put ubuntu first on the disk, and therefore changed the start of that XP partition to a different sector and block on the disk, that could account for the problem.  If you simply sliced those 10GB from the right hand end of the XP partition, it should have worked fine, though whenever I did such operations, I always booted back into windows before installing anything else, in order to let windows run chkdisk at boot, which it always needed to.

I hope your system recovery works!

---

### Post by lykwydchykyn on 2012-07-14
Well, the bad news is the system recovery didn't fix it.

The good news is, I managed to do it. 

I booted to partedmagic, ran testdisk and repaired the bootsector and MFT.

Windows now boots fine.  Xubuntu is still on there, but we have no way to boot to it now.  I'd rather not mess with the MBR any more, so I'm going to attempt to load it from the Windows bootloader.

---

