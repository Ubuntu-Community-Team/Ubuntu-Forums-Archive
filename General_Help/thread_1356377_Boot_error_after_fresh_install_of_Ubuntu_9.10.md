---
title: "Boot error after fresh install of Ubuntu 9.10"
date: 2009-12-16
forum: General Help
---

### Post by dobbod on 2009-12-16
Hi, recently I received Ubuntu 9.10 CD Desktop Edition. During the install, I deleted all partitions of  Ubuntu 9.04 and do fresh install of 9.10. Everything was okay, installed succesfully, but when it comes to reboot, below message appeared:

```

Common problems:
- Boot args (cat / proc / cmdline)
- Check rootdelay = (did the system wait long enough?)
- Check root = (did the system wait for the right device?)
- Missing modlues (cat / proc / modules; ls / dev)
ALERT! / dev / disk / by-uuid / xxxxxxxxxxxxxxxxxxxxxxxxx does not exists. 
Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

```For these few days, I have tried several solutions recommended by some other Ubuntu users, but it seems like the  luck is not on my side.

I've also tried these (at the boot option):
1. Extend rootdelay=120
2. Change uuid no from xxxxxxx (quite long) to / dev/sda3.
3. Change root=(hd0,3) to root=/dev/sda3

This is some more info:
- Windows XP in partition sda1
- Ubuntu 9.10 with kernel 2.6.31.16, root (sda3), home (sda4), and swap (sda 8 ).
- There are 2 hardisks: 320 GB (I put Ubuntu and Xp here) and 640 GB (as data).
- I Can boot into live-cd only if this string is inserted: all_generic_ide floppy=off irqpoll pci-nomsi

I've tried many solved issues, recommended methods, but still I can't boot into Ubuntu 9.10. So, I think it's time for me to open new thread for my case. I really appreciate for any help. 

Thank you.

dobbod

---

### Post by dobbod on 2009-12-17
Please help. I really want to use Ubuntu as my primary OS.

This is some more info I got through Live-CD:

```
ubuntu@ubuntu:~$ sudo blkid

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="0C7C62BC7C62A066" TYPE="ntfs" 
/dev/sda3: UUID="d753de8b-7a5e-493d-9983-1a861de4246c" TYPE="ext4" 
/dev/sda4: UUID="b0ab4a34-ea38-4434-b1cf-f287d5584600" TYPE="ext4" 
/dev/sda5: UUID="EEB42BEFB42BB8CB" LABEL="Program" TYPE="ntfs" 
/dev/sda6: UUID="568497A4849784E1" LABEL="Docs" TYPE="ntfs" 
/dev/sda7: UUID="4E4CB1184CB0FBB1" LABEL="OS Bkp" TYPE="ntfs" 
/dev/sda8: UUID="7e931233-94be-49d3-a1f3-7c811d7f4e4c" TYPE="swap" 
/dev/sdb1: UUID="60F84380F8435386" LABEL="Data" TYPE="ntfs" 
/dev/sdb5: UUID="92DC4B11DC4AEF53" LABEL="Backup" TYPE="ntfs" 
``````
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe531e531

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2612    20980858+   7  HPFS/NTFS
/dev/sda2            2613       33110   244975185    f  W95 Ext'd (LBA)
/dev/sda3           33111       34355    10000462+  83  Linux
/dev/sda4           34356       38913    36612135   83  Linux
/dev/sda5            2613       15669   104880321    7  HPFS/NTFS
/dev/sda6           15670       29377   110109478+   7  HPFS/NTFS
/dev/sda7           29378       32986    28989261    7  HPFS/NTFS
/dev/sda8           32987       33110      995998+  82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45d086da

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       58744   471861148+   7  HPFS/NTFS
/dev/sdb2           58745       77825   153268132+   f  W95 Ext'd (LBA)
/dev/sdb5           58745       77825   153268101    7  HPFS/NTFS
ubuntu@ubuntu:~$ 
```

---

### Post by Sin@Sin-Sacrifice on 2009-12-17
I would change back to UUID and (hd0,3) and give [these]("http://samiux.wordpress.com/2008/12/16/howto-avoid-to-drop-to-busybox-in-ubuntu-810/") a try. Also check out [these results]("http://www.google.com/#hl=en&source=hp&q=Ubuntu+drops+to+busybox&aq=f&aqi=&oq=&fp=b36c7832dbb01be6") for, perhaps, other solutions.

---

### Post by dobbod on 2009-12-17
> **Sin@Sin-Sacrifice said:**
> I would change back to UUID and (hd0,3) and give [these]("http://samiux.wordpress.com/2008/12/16/howto-avoid-to-drop-to-busybox-in-ubuntu-810/") a try. Also check out [these results]("http://www.google.com/#hl=en&source=hp&q=Ubuntu+drops+to+busybox&aq=f&aqi=&oq=&fp=b36c7832dbb01be6") for, perhaps, other solutions.
Yes, problem solved !! :)

Thanks for your tips, Sin@Sin-Sacrifice. They really helped me especially the google search results, where I found a tips to edit my grub with the correct string (refer to fourth post [COLOR=Blue][in this thread]("http://ubuntuforums.org/archive/index.php/t-1140101.html")[/COLOR]).

What I did was:

In the grub menu, press "e" to edit the kernel boot string', from

> recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 1751283b-b905-49fb-bc81-93e2e561bfd9
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=1751283b-b905-49fb-bc81-93e2e561bfd9 ro    quiet splash
    initrd    /boot/initrd.img-2.6.31-14-genericchange to:

> recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 1751283b-b905-49fb-bc81-93e2e561bfd9
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=1751283b-b905-49fb-bc81-93e2e561bfd9 ro    quiet splash [COLOR=Red]**all_generic_ide floppy=off irqpoll pci=nomsi**[/COLOR]
    initrd    /boot/initrd.img-2.6.31-14-genericThen, "ctrl+x" to boot and I can boot into Ubuntu 9.10 happily...


To change that permanently, we have to edit the grub file.

```
sudo etc/default/grub
```Add the last line, like this:

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
[COLOR=Red]**GRUB_CMDLINE_LINUX="all_generic_ide floppy=off irqpoll pci=nomsi"**[/COLOR][COLOR=Red][COLOR=Black]Then run update-grub2[/COLOR][/COLOR]

```
sudo update-grub2
```

---

