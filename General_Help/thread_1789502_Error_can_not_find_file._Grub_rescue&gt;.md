---
title: "Error: can not find file. Grub rescue&gt;"
date: 2011-06-23
forum: General Help
---

### Post by DRSorensen on 2011-06-23
I installed ubuntu 11.04 via the Wubi installer about a month ago (with Vista). It's been working fine, but today I was copying a file from a flash drive and it froze up. At first it was just the progress bar, then the unity bar and desktop, and eventually the mouse. I turned it off then on again to find that when I chose ubuntu from the startup menu I got the following error (could still boot into Vista):
[FONT=Courier New]
mount: mounting /dev/disk/by-uuid/a3c31122-6794-4fa6-a039-91d49dadfa8a on /root
failed: Invalid argument
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init = bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a lit of built in commands.

(initramfs)[/FONT]

There are numerous online posts describing this error, and no definite answers. Luckily I already had made a "liveCD" on a USB drive.

Output of [FONT=Courier New]sudo fdisk -l[/FONT]:
[FONT=Courier New]
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: **********

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7296    58602496    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 4047 MB, 4047502848 bytes
4 heads, 32 sectors/track, 61759 cylinders
Units = cylinders of 128 * 512 = 65536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       61760     3952623+   b  W95 FAT32
[/FONT]
[FONT=Verdana](I assume the WARNING and stuff about /dev/sdb is from the USB drive I booted from)

As you can see, it only shows 1 partition, /dev/sda1.  Following the advice of a couple different forum posts, I tried a [/FONT][FONT=Courier New]sudo mount /dev/sda1 /mnt[FONT=Verdana], followed by [FONT=Courier New]sudo grub-install --root-directory=/mnt/ /dev/sda [FONT=Verdana]and [/FONT][/FONT][/FONT][/FONT][FONT=Courier New]sudo update-grub[/FONT].

[FONT=Verdana]There was some kind of error, which I can't remember...

Now[/FONT] when turn on the laptop it goes through the Dell loading screen, then gives me the error (before I even get to the boot menu, so I can't even get into Vista):

[FONT=Courier New]Error: can't find file

Grub rescue>

[FONT=Verdana](Grub rescue> is some kind of prompt, not sure what to do with it though)


Anyway, now I can't get into ubuntu OR vista. I can only boot it from my USB drive.

I'd really like to not loose all my data. Does anybody have any idea what I should do?
[/FONT][/FONT]

---

### Post by bcbc on 2011-06-23
You want to avoid installing grub if you are using Wubi. Wubi boots via the windows boot manager, and windows requires a windows style bootloader to boot.

So check out the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") Problem #1, solution #1 or #2 to get Vista booting again.

That will get you back to where you were before - vista booting but not wubi. To fix Wubi - it seems like you'll need to fsck your root.disk. Boot from the live USB again, then:
```
sudo mount /dev/sda1 /mnt
sudo fsck /mnt/ubuntu/disks/root.disk
sudo umount /mnt
# reboot and try to boot your Wubi Ubuntu again
sudo reboot
```

That will probably do it. 

Avoid hard power-offs on Ubuntu. Even if it seems like it's hanging - sometimes it isn't and you can corrupt the root.disk easily. In some cases, Windows will remove it - if the file looks corrupted under ntfs. So you can lose everything on it.
Instead, first try to shut down safely with Alt+Sysrq R-E-I-S-U-B (use PrntScr if no SysRq)

---

### Post by DRSorensen on 2011-06-24
Thank you for your timely reply. In part of installing lilo to get Vista to boot, I had to reboot the laptop. 

It gave me the option to choose Vista or ubuntu, like it usually does (but didn't because of the grub rescue error). 

I tried booting into ubuntu and... Whad'ya know? It worked!

Thanks anyway for the effort of trying to help :D

---

### Post by bcbc on 2011-06-24
> **DRSorensen said:**
> Thank you for your timely reply. In part of installing lilo to get Vista to boot, I had to reboot the laptop. 

It gave me the option to choose Vista or ubuntu, like it usually does (but didn't because of the grub rescue error). 

I tried booting into ubuntu and... Whad'ya know? It worked!

Thanks anyway for the effort of trying to help :D

Great. Happy to help.

Just remember the part about not hard-powering-off - and consider keeping important data backed up outside Ubuntu (i.e. the root.disk) e.g. on /host or some external drive.

---

