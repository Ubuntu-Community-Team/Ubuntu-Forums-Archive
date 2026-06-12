---
title: "USplash not working right after relocating Ubuntu to a different hard drive?"
date: 2009-07-26
forum: General Help
---

### Post by Joshw91 on 2009-07-26
Hello everyone!

I'm new to ubuntu forums and I have a small problem. It's not much more than annoying to me, everything else works fine, but USplash isn't working correctly.
During boot, the normal boot splash screen shows up and the loading bar moves back and forth, then instead of showing a growing orange bar in the second stage, it goes into a verbose text mode showing the output of init.d. I suspect there is something that I didn't do when moving Ubuntu to a different hard drive. I'll list the steps I took, and hopefully you can come up with what I can't figure out myself.


[LIST=1]
[*]Running Ubuntu in my old partiton, I partitioned out my new hd with ext4 and a swap partition.
[*] I copied all of the files to the new hard drive, preserving permissions, etc.
[*] I updated /etc/fstab (I think) and grub's menu.lst to point to the new hd. (I also updated the swap partition in fstab.)
[*] I ran grub-install to reconfigure grub.
[*] I rebooted and everything seems to work fine to this day, except usplash.
[*]I, of course, deleted the old partition and resized my vista partition to utilize the whole first disk.
[/LIST]
So, I believe I need to configure USplash somehow because it must still think something is located at the old, nonexistent partition. I can't find out how to configure it, though.

OR, the reason could be totally unrelated to my relocation and therefore I did it perfectly :P

Any help is appreciated! I'll keep trying to figure this out in the meantime and keep this thread updated. Thanks for your help! :D
Josh

---

### Post by plucky on 2009-07-26
Open a terminal and use ```
sudo update-initramfs -u -k all
``` should update the initramfs for all you kernels.Could take a while if you have a number of previous kernels.


If that doesn't work,open a terminal and post output of ```
 cat /etc/initramfs-tools/conf.d/resume
sudo blkid -c /dev/null
cat /etc/fstab
cat /boot/grub/menu.lst
```

and post between [noparse]```

```[/noparse] brackets.


It could be caused by a UUID being different in one of these files.

Good Luck

---

### Post by Joshw91 on 2009-07-27
Thanks for your help! Everything works perfectly now, the file I needed to update was /etc/initramfs-tools/conf.d/resume! :D I tried update-initramfs before, but unaware of that file. Perhaps now a complete tutorial could be written on relocating an Ubuntu installation?

---

