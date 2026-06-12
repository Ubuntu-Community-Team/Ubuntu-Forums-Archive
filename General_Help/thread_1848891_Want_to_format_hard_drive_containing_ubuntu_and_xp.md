---
title: "Want to format hard drive containing ubuntu and xp"
date: 2011-09-23
forum: General Help
---

### Post by ltwinner on 2011-09-23
I have a dual boot system, ubuntu and xp and it uses grub bootloader. I want to completely wipe this and install windows 7 instead and run ubuntu through virtualbox as that is what i am doing all the time anyway at the moment with xp. I need to work with ubuntu and windows simultaneously, so I never actually boot into ubuntu, I just use virtualbox.

So what is the procedure for completely removing both operating systems (and grub?) so i can have a blank harddrive?

---

### Post by Elfy on 2011-09-23
If you're going to install windows I would be inclined to boot the livecd - start the partition editor - system admin menu (or type it in the dash thing in unity) 

Right click on swap and swap off if it's being used - make sure all partitions are unlocked - delete them, format it to ntfs and boot the windows cd.

Or alternatively just delete them and let the windows cd find an empty drive.

---

### Post by Mark Phelps on 2011-09-23
forestpixie is right ...

Although, in principle, you SHOULD be able to boot from a Win7 Install DVD and reformat your entire drive, LOTS of folks have reported problems trying to do that, with the most common one being that Win7 was unable to find any hard drives!

So, removing the partitions from your drive is the safest bet.

---

### Post by coffeecat on 2011-09-24
> **ltwinner said:**
>  (and grub?)

Just to add... Don't worry about grub in the mbr. The Windows installer will write its own mbr code, overwriting the grub code.

---

