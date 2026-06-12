---
title: "GRUB Reinstallation"
date: 2009-08-06
forum: General Help
---

### Post by guguma on 2009-08-06
This is a classic issue which I seems I screwed up.

I reinstalled windows and thus grub is gone. I booted into a crunchbang linux (ubuntu variant, I do not have ubuntu live at hand) livecd and used (all executed as root)

```
grub-install -root--directory=\media\ubuntu hd0
```

\media\ubuntu is the directory I mounted my ubuntu root on the livecd.

I did not backup my menu.lst so I only get a grub prompt when I boot. Now 3 questions

1. I want menu.lst again with ubuntu boots and the chainloader +1 (for ntloader) I can create a menu.lst and make grub use that list there was a command for that but I have no idea how to write the menu.lst.

2. The better option is if there is a way for grub to look for possible boots and create the list for me? Would alternate install cd's grub installation do that for me? (I will need to download the cd though.)

3. This might be irrelevant but I also tried fixmbr from windows repair thingy(before I kinda figured out how to boot from grub command prompt), it told me it did repair the mbr at \device\HardDisk1\Partition0, but I got grub as my bootloader again? is what windows calls as HD1P0 the same as what Unix calls as (hd0, 0) or is there some foul integer play here? If they are the same locations why would fixmbr fail at overwriting grub?

Thanks in advance.

---

### Post by martinbaselier on 2009-08-06
Your grub menu should normally still be in /boot/grub/menu.lst on the ubuntu partition. If you mount from the livecd the location would be:
/media/ubuntu/boot/grub/menu.lst

So it seems grub does not have the right device. 

You can use /dev/??? instead of hd0
**sudo fdisk -l** will show you the available disks. This will help you to make the right choice.

---

### Post by guguma on 2009-08-06
> **martinbaselier said:**
> Your grub menu should normally still be in /boot/grub/menu.lst on the ubuntu partition. If you mount from the livecd the location would be:
/media/ubuntu/boot/grub/menu.lst

So it seems grub does not have the right device. 

You can use /dev/??? instead of hd0
**sudo fdisk -l** will show you the available disks. This will help you to make the right choice.

I used grub-update to create a menu.lst file, now I managed to make grub boot windows, but I cannot boot ubuntu, the problem is grub-install overwrites "/boot" and because ubuntu keeps the initrid.img and vmlinuz.img at /boot they are gone? I found a vmlinuz and initrid.img at / but they do not seem to work? (EDIT: I think they are symlinks and that is why they do not work, the actual thing is not there?)

is there a workaround for this or should I reinstall ubuntu?

---

### Post by mhbell on 2009-08-14
I had the same problem with Ubuntu 9.04 I finally gave up and reinstalled Ubuntu 9.04
Mel
:(

---

