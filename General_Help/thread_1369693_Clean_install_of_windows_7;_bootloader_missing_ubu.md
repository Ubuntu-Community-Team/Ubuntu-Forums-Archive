---
title: "Clean install of windows 7; bootloader missing ubuntu"
date: 2010-01-01
forum: General Help
---

### Post by sekhar.b on 2010-01-01
Hello,

A couple of months ago I decided to use the wubi installer to install ubuntu on my comp in a dual boot configuration.

Yesterday, I clean installed my windows drive with windows 7.

The good news:
I have my windows install on drive C: and my wubi install in Drive D: ( they are on completely different hard disks ), so the ubuntu virtual disks are still intact and the wubildr.mbr is still there.

The bad news: 
The bootloader screen at startup doesn't appear at all! I tried to manually boot into the D: hard drive but come up with a error 17 grub loading error, which was because the grub loader doesn't recognize the file system on the drive (ntfs).

So my question is: is there a way to somehow recover the wubi installation?

Thanks in advance!

EDIT:
Okay, I did some research on the net, apparently if I backup up the root.disk file, erase everything else on the drive, install wubi again and overwrite the root.disk file with the backed up one I should be able to restore my previous ubuntu installation!
However, I don't want try something until I'm certain that it would work, so can any expert confirm that this is a a valid solution, and if not give me another suggestion!

Thanks!

---

### Post by sekhar.b on 2010-01-02
no one.....? :(

---

### Post by Mark Phelps on 2010-01-02
Whenever you install an MS Windows app, it writes info into a collection of database files known as the Windows Registry.  When you clean-installed Win7, it completely wiped out the registry and replaced it with a fresh one.  Thus, any entries there for Wubi were gone.

When you reinstall Wubi, that should rewrite the registry entries, and when you overwrite the disk file, that should replace that with your original install.  So, it should be OK.

Also ...

Wubi does not use GRUB; it uses GRUB4DOS because it writes the entries to an NTFS partition -- which GRUB  could not use.  So, attempting to use GRUB to repair Wubi is a waste of time.

---

### Post by MooPi on 2010-01-02
I would suggest that if your still interested in using Ubuntu, do a clean install . Download and burn the CD image to disk and install. If you have already saved your home directory then it should be a simple transition.

---

