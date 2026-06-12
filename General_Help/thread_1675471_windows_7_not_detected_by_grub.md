---
title: "windows 7 not detected by grub"
date: 2011-01-25
forum: General Help
---

### Post by Julius1988 on 2011-01-25
I recently installed ubuntu in my dell inspiron n series, after installation only ubuntu is in grub configuration. Windows is not detected by grub. 

Here is what i get if i do *fdisk -l*
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9807    78774696    7  HPFS/NTFS
/dev/sda2            9808       60802   409610778    f  W95 Ext'd (LBA)
/dev/sda5            9808       22555   102398278+   7  HPFS/NTFS
/dev/sda6           23861       35303    91908096    7  HPFS/NTFS
/dev/sda7           35304       48051   102398278+   7  HPFS/NTFS
/dev/sda8           60252       60802     4415488   82  Linux swap / Solaris
/dev/sda9           48052       60251    97995776   83  Linux

Partition table entries are not in disk order


```

Here is what i get after doing *update-grub*.
```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done

```

In the above execution there is no indication of windows being detected.

Why it is not getting picked up by the grub?

---

### Post by Mark Phelps on 2011-01-26
You have to do "sudo update-grub".  Sudo is required in order for the command to work.  The error message you're getting implies you ran it without using "sudo".

---

### Post by Quackers on 2011-01-26
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Robbinski12 on 2011-06-09
Sorry for reviving this thread, but I'm having this exact same problem. I did what was mentioned before, here is my RESULTS.txt:
[http://www.pastie.org/2044251](http://www.pastie.org/2044251)

Thanks in advance!
Robin

---

### Post by drs305 on 2011-06-09
> **Robbinski12 said:**
> Sorry for reviving this thread, but I'm having this exact same problem. I did what was mentioned before, here is my RESULTS.txt:
[http://www.pastie.org/2044251](http://www.pastie.org/2044251)

Thanks in advance!
Robin

The RESULTS.txt found the following boot files/folders for Windows:
>  Boot files:        /Windows/System32/winload.exe
It did *not* find two folders Windows needs:
>  /bootmgr /Boot/BCD
Without these entries, I don't know that Windows would boot, and I do know that it will prevent Grub in many cases from identifying the Windows OS since it looks for these files/folders to identify a bootable Windows OS.

I'll leave it to the Windows guys to suggest a course of action to repair Windows.

---

### Post by Robbinski12 on 2011-06-10
Thanks anyway for your reply!

---

### Post by drs305 on 2011-06-10
I'd hoped someone would have jumped in. But anyway, here is one of the 'standard' links for repairing Windows:
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by Quackers on 2011-06-10
Your sda2 partition is not mounting. It appears to be a Linux partition but we don't know what's in it.
Sadly, the boot flag is set on that partition. It needs to be moved to the sda3 partition (with gparted perhaps) before the repairs will work.
Do you have a Windows 7 repair disc (or an installation disc)?

---

### Post by Robbinski12 on 2011-06-12
No, but I could use one of our other computers to make one...

EDIT: Did I mention that the Windows drive mounts in Ubuntu labeled 'Packard Bell', dunno if it's relevant, though..

---

