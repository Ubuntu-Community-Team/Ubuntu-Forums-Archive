---
title: "Dual Booting Question"
date: 2009-12-29
forum: General Help
---

### Post by CrusaderAD on 2009-12-29
Let's say I have two partitions. A 50gig, B 50gig. If I install Windows on A, boot up with a blank "D" 50 gig drive, then run the Live Ubuntu cd and install the Ubuntu OS on the B 50gig, will it effect drive A in anyway? I did do this at one point and noticed that the boot loader that loads up is the Linux version (where I can pick what to boot into). Does this matter? What if I formatted drive B and removed linux, would the windows boot loader take over once that drive is blank again?

---

### Post by konqueror7 on 2009-12-29
> **raptormanad said:**
> Let's say I have two partitions. A 50gig, B 50gig. If I install Windows on A, boot up with a blank "D" 50 gig drive, then run the Live Ubuntu cd and install the Ubuntu OS on the B 50gig, will it effect drive A in anyway? I did do this at one point and noticed that the boot loader that loads up is the Linux version (where I can pick what to boot into). Does this matter? What if I formatted drive B and removed linux, would the windows boot loader take over once that drive is blank again?

if i read correctly, only A and B have OSs installed, and D plays no role as i see it. yes, when you install Linux after Windows, it will create a boot loader for your (GRUB/2), which will overwrite your current Windows MBR. when removing Linux in B, you have to restore the MBR. you may do this by using Windows's recovery disc and doing a repair, or using [Ubuntu's livecd]("http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/").

---

### Post by CrusaderAD on 2009-12-29
Thanks for the reply. Is there anyway to not overwrite the windows MBR when installing Ubuntu?

---

### Post by konqueror7 on 2009-12-30
> **raptormanad said:**
> Thanks for the reply. Is there anyway to not overwrite the windows MBR when installing Ubuntu?

i think not, while windows itself don't allow other OSs installed, so the only way is to overwrite the MBR and use a bootloader. windows has also a bootloader, works for other windows OSs.:)

---

