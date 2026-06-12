---
title: "will grub be installed if windows and ubuntu are on separate physical disks?"
date: 2010-01-14
forum: General Help
---

### Post by Andreas1 on 2010-01-14
up to now i've only had one hard disk, and i am about to install ubuntu to the second hard disk (sata) on a system where on the first hard disk there is windows xp. will grub be installed, and will both systems be added to the grub menu? or is it common to choose between them via bios boot order?

---

### Post by lorsen on 2010-01-14
I never tried, but my feeling say it works the same as when you only have one physical disc with two partitions and I never heard of someone changing boot priority to switch operating systems.

But I guess someone will give a more confident answer.

---

### Post by john newbuntu on 2010-01-14
I too feel that the default installation of Grub is on the MBR of first disk unless you change it, which means both systems will be available to you via the Grub2 menu when you boot your PC.
You could alternately write Grub to the MBR of second disk during the last process before installation actually begins.  You would then want to change BIOS boot order to decide on which OS to boot.

---

### Post by reiki on 2010-01-14
I've done this both ways.
Changing boot order in BIOS is a really clunky way to multi-boot. Let GRUB install to the MBR of the primary boot device. 

Be sure to LEARN ABOUT GRUB so you know how it works and how to make changes if you want. 

If you have SATA#1 with XP and SATA#2 with Ubuntu, you can install GRUB to the MBR on SATA#2 and then switch boot order so SATA#2 becomes the primary boot device. If you really run into trouble at some point, you could then change primary boot device to SATA#1 and it should boot to XP as it does now with the single hard drive.

Choosing you OS by entering BIOS is really not the way to go, in my opinion.

---

### Post by Andreas1 on 2010-01-14
> **reiki said:**
> I've done this both ways.
Changing boot order in BIOS is a really clunky way to multi-boot. Let GRUB install to the MBR of the primary boot device. 

Be sure to LEARN ABOUT GRUB so you know how it works and how to make changes if you want. 

If you have SATA#1 with XP and SATA#2 with Ubuntu, you can install GRUB to the MBR on SATA#2 and then switch boot order so SATA#2 becomes the primary boot device. If you really run into trouble at some point, you could then change primary boot device to SATA#1 and it should boot to XP as it does now with the single hard drive.

Choosing you OS by entering BIOS is really not the way to go, in my opinion.

ok, so grub will be installed to sata#2 during default installation, it will include windows too, and i just direct the bios to sata#2. thank you!

---

