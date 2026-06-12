---
title: "Boot with quiet splash"
date: 2009-09-18
forum: General Help
---

### Post by Jaraxle on 2009-09-18
Hi all,

I am running Jaunty, just installed on a new hard drive. I am dual-booting with Windows XP. One of the things I liked was how fast and clean the boot process was for Ubuntu.

Now, however, the quiet startup will show the text messages related to bootup. Not all of them, it will show the splash screen for awhile, then show messages, then go to a blank screen, then back to splash screen before loading the desktop. The startup is also taking a little longer.

This started after I grew the size of my partition for Ubuntu, by booting with the live CD after first shrinking the partition size for Windows. It did give 4 warnings after completing both operations, but didn't say what they were.

I installed Startup Manager using apt-get, and no matter what I try I can't get it back to quiet splash. I also tried editing from the Grub menu at boot time.

I'm really picky about how things look on my computer. I want my nice, quiet splash screen back! Can anyone help me? I guess I can reinstall Ubuntu, but I really don't want to. There must be a way to get it back.

---

### Post by plucky on 2009-09-18
> **Jaraxle said:**
> Hi all,

I am running Jaunty, just installed on a new hard drive. I am dual-booting with Windows XP. One of the things I liked was how fast and clean the boot process was for Ubuntu.

Now, however, the quiet startup will show the text messages related to bootup. Not all of them, it will show the splash screen for awhile, then show messages, then go to a blank screen, then back to splash screen before loading the desktop. The startup is also taking a little longer.

[color=blue]This started after I grew the size of my partition for Ubuntu, by booting with the live CD after first shrinking the partition size for Windows.[/color] It did give 4 warnings after completing both operations, but didn't say what they were.

I installed Startup Manager using apt-get, and no matter what I try I can't get it back to quiet splash. I also tried editing from the Grub menu at boot time.

I'm really picky about how things look on my computer. I want my nice, quiet splash screen back! Can anyone help me? I guess I can reinstall Ubuntu, but I really don't want to. There must be a way to get it back.


The UUID of your partition has probably changed.Post output of ```
sudo blkid
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
sudo fdisk -l
```

Good Luck

---

### Post by nico_forgot on 2009-09-18
what does your /boot/grub/menu.lst file have listed where i've placed "HERE?"

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions= HERE

if quiet splash isn't listed edit it in. it's a /boot file so you'll need to edit it under sudo.

a though :)

---

### Post by Jaraxle on 2009-09-19
Well, earlier today I decided to just go ahead and reinstall to take care of the problem. It's back to normal now.

Thanks for the help, though. I guess this thread can be closed.

---

