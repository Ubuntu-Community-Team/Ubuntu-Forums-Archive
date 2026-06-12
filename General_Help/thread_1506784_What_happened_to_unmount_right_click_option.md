---
title: "What happened to unmount right click option?"
date: 2010-06-10
forum: General Help
---

### Post by Nonno Bassotto on 2010-06-10
After upgrading from 9.10 to 10.04 I'm left without the right click menu entry for unmounting USB disks. The only graphical way I can do it is by clicking the eject button in Nautilus.

Is there a way to get back the menu entry? Why was this even changed?

---

### Post by dcstar on 2010-06-12
> **Nonno Bassotto said:**
> After upgrading from 9.10 to 10.04 I'm left without the right click menu entry for unmounting USB disks. The only graphical way I can do it is by clicking the eject button in Nautilus.

Is there a way to get back the menu entry? Why was this even changed?

Because there is little point in just unmounting a removable drive partition, that is why "Safely Remove Drive" is there.

---

### Post by inameiname on 2010-06-12
I only lost it in the past week in Lucid for some reason. Some update changed things.

Oh, and one reason to 'unmount' and not 'safely remove' is if you want to unmount before erasing a CD or DVD rewriteable, or perhaps a USB drive using Gparted.

---

### Post by doas777 on 2010-06-12
> **inameiname said:**
> I only lost it in the past week in Lucid for some reason. Some update changed things.

Oh, and one reason to 'unmount' and not 'safely remove' is if you want to unmount before erasing a CD or DVD rewriteable, or perhaps a USB drive using Gparted.
so far as I am aware, the two ops are the same. safely remove just commits the write cache and dismounts the volume. perhaps there is somthing more to it.

---

### Post by inameiname on 2010-06-12
"Safely Remove' completely turns off the device's power, and turns it off to essentially appear as if it isn't even connected. As such, Gparted won't even notice it as plugged in, however with just unmounting it, which can still be done for me through Disk Utility, Gparted recognizes it just fine, and I can also use say the 'shred' command through the terminal to erase it. Power is still there and it's still 'plugged in' according to the operating system using just 'unmount.' 

Oh, and if it is perhaps an SD card, if you 'safely remove' it, it literally turns off the device entirely, the hardware of the built-in reader, and no matter if you pop back in another SD card or whatever, you can't get it to work until you restart the computer. Whereas with just an 'unmount', you can push it back in or replace it with another, and voila, it's read and a window pops up.

---

### Post by Nonno Bassotto on 2010-06-12
Safely remove is fine for me. The problem is that it doesn't work on multiple selections, and since my disk has two partitions, I never realized it existed. I just have to unmount the partitions one at a time.

---

