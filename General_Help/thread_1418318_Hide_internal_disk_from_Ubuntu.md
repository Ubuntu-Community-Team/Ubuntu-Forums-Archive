---
title: "Hide internal disk from Ubuntu?"
date: 2010-02-28
forum: General Help
---

### Post by Jack.Bauer on 2010-02-28
Hello,

I installed the Ubuntu 9.1 on a USB hard drive on my laptop.  The laptop is running XP, with all NTFS partitions.

When I installed Ubuntu, I pulled the internal drive so as to not make a mistake and overwrite my main OS.

Interestingly - now if I pull the internal drive and try to boot off the USB with no internal drive present, Ubuntu will not load.  It will load fine on the USB if the internal laptop HD is there.  That's another problem that I really am not concerned with right now though...

The internal drive is NOT in /etc/fstab

What is frustrating the heck out of me, is that I cannot find a way to force Ubuntu to NOT see my internal drive at all.  While it does not automatically mount the internal drive, as I said - it won't boot without it...  And it shows up in the disk utility, and I have no problem mounting it, and reading and writing to it.

I want to completely separate that hard drive - not because I'm afraid someone's going to break into it...  I just want to do everything possible to prevent "something from going wrong" somewhere, and Ubuntu accessing those NTFS drives.

I've read some other threads and from what I can tell, it seems to be impossible to remove NTFS support from the current version.  Is that indeed correct?

Would I actually have to switch to another Linux flavor in order to completely lose NTFS support?

Thank you for your time :)

Jack

---

### Post by falconindy on 2010-02-28
Sounds like GRUB (the bootloader) is installed to the disk that you're pulling.

Ironically, I think the best way to 'hide' the drive is to add it to fstab. Make sure you add the 'noauto' option.

---

### Post by Jack.Bauer on 2010-02-28
Thanks...

But I don't think that is it.

I am selecting the USB boot device on my boot menu.

Also I imagine if grub installed to my main hard drive - that it may have hurt my safeboot installation on that drive.

---

### Post by falconindy on 2010-02-28
If you're seeing Grub's menu, then it's an issue with the root device numbering when the other drive isn't present. You can fiddle with this from within Grub2 by editing the appropriate entry.

> Also I imagine if grub installed to my main hard drive - that it may have hurt my safeboot installation on that drive.
I strongly disagree with this. Assuming by 'safeboot' you mean the manufacturer provided recovery partition, you can install Grub to the **MBR** without harming the **partition**.

---

### Post by Jack.Bauer on 2010-02-28
> **falconindy said:**
> If you're seeing Grub's menu, then it's an issue with the root device numbering when the other drive isn't present. You can fiddle with this from within Grub2 by editing the appropriate entry.


I strongly disagree with this. Assuming by 'safeboot' you mean the manufacturer provided recovery partition, you can install Grub to the **MBR** without harming the **partition**.

I'll have to take a look at Grub2 per your recommendations.

Safeboot, meaning the whole drive encryption program that won't let me boot windows without entering the proper password.

---

### Post by asmoore82 on 2010-02-28
You need to add all of the NTFS partitions to /etc/fstab and make sure to use the noauto and nouser options.
This will effectively keep them from mounting at boot and hide them from the User-Friendly mounting services.

---

### Post by sgosnell on 2010-02-28
You can't hide drives from Ubuntu, it will find every drive installed, by design.  It won't necessarily mount them, but it will find them.  If a drive is not mounted, then it can't be written to, so just don't mount your internal drive and all will be well.  

Since you removed the internal drive for the install, the installer thought that the external drive was sda1.  When you reinstalled the internal drive, it became sda1, because internal drives are always labelled before external drives.  GRUB wants to boot from sda1 because that's what it was told to do during the install.  Now it needs to boot from (perhaps) sdb1.  You need to boot to Ubuntu and reinstall GRUB.  There are several tutorials available, depending on the version you have installed currently.  Just make sure you get it on the external drive, and do not remove the internal drive, or you'll end up back where you started.

---

