---
title: "GRUB would not allow to boot from Live CD"
date: 2011-08-11
forum: General Help
---

### Post by ssreddy555 on 2011-08-11
I have a quad boot system with Win 7, Ubuntu 11.04, Mint 11 - 64 bit  &  Mint 11 - 32 bit.

Now, I want to test Android OS on pc with a live CD. I downloaded an iso file & burnt it to CD.

Although I set the 1st boot priority to CD drive, it does not boot from the CD; The usual GRUB menu is displayed. 

How to boot from CD in this situation?

I have also tried after disabling the HDD in BIOS; then it gives out the prompt to insert a bootable medium although the CD is in the drive & the CD Drive is the only place from which booting can take place now because the HDD is disabled. I think GRUB will not be detected now as the HDD is disabled, isn't it?

---

### Post by garvinrick4 on 2011-08-11
If disk is a bootable disk and CD drive is set to boot before HDD and it does not, something
is not right with bootable disk.
Grub has not hit yet so not its problem, Bios hits before grub. Grub is in mbr of disk (master boot record). 
Try a different disk.

---

### Post by arubislander on 2011-08-11
> **ssreddy555 said:**
> Now, I want to test Android OS on pc with a live CD. I downloaded an iso file & burnt it to CD.

When you open your CD to show it's contents in the filemanager. Do you see more than one file, or only the iso file?

---

### Post by ssreddy555 on 2011-08-11
yes, there was a problem with the file on the CD.

Further, I downloaded the iso file again & tested this time through the usb drive, using unetbootin.

This time, it worked but it was not really worth it.

Thanks both of u.

---

### Post by drs305 on 2011-08-11
> **ssreddy555 said:**
> 

This time, it worked but it was not really worth it.

Thanks both of u.

If you don't need any further assistance with this issue please mark the thread 'SOLVED' via the 'Thread Tools' link near the top right of the first post.  Thanks.

---

