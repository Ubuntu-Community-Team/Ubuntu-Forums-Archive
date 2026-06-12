---
title: "[curiosity] Boot time depending on number of dsks?"
date: 2009-09-24
forum: General Help
---

### Post by ilpiero on 2009-09-24
Hi all, i have a simple question for someone who knows linux better than me.
I'm using ubuntu jaunty 64 bit on a pretty new computer, and after adding a secondo 300 gb sATA disk (ext4 formatted only for storage purpose, added to the fstab list) i experience a noticeable increase of the boot time (6-7s viewing the ubunto splash screen bar ).

Is this an expected normal behaviour or is there something wrong?

Thank you!

---

### Post by DFlame on 2009-09-24
If it all works correctly when it does boot up, I don't see the problem with waiting a few more seconds ;)

As for why it takes longer, I know what the BIOS has to detect the drive, Linux has to detect the drive and then mount it too, as it is in the fstab. Your BIOS may also look for a non-existant boot record on the drive, which could increase start time. 

There's probably more things that could be affected, but I'd stick with Ain't broke/Don't fix :D

---

### Post by ilpiero on 2009-09-24
> **DFlame said:**
> If it all works correctly when it does boot up, I don't see the problem with waiting a few more seconds ;)


there is no problem, just asking ;)

> **DFlame said:**
> 
As for why it takes longer, I know what the BIOS has to detect the drive, Linux has to detect the drive and then mount it too, as it is in the fstab. Your BIOS may also look for a non-existant boot record on the drive, which could increase start time. 

There's probably more things that could be affected, but I'd stick with Ain't broke/Don't fix :D

ty 

Bye!!

---

