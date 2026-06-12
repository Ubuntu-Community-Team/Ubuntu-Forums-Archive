---
title: "Grub2 won't load Windows"
date: 2011-05-16
forum: General Help
---

### Post by peacebreaker on 2011-05-16
Here is the story, i installed ubuntu / under /dev/sda1, then installed Win7 under /dev/sda2, as primary. Extended partition and its logicals are for data.

After Win7 installation, i can restore the grub2 for ubuntu, with grub-install and update-grub2. It can even probe the NTFS partition under /dev/sda2. But at restart, when i tried to go to Win7 selection, it does nothing, screen goes black, blank, with a single cursor blinking.

What went wrong and how to fix?

Some data:

Ubuntu Natty 11.04

From /etc/grub/grub.cfg:
```


menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(/dev/sda,msdos2)'
        search --no-floppy --fs-uuid --set=root 0A75D1E20126EB56
        makeactive
        chainloader +1
}

```

From fdisk -l:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3b330707

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2566    20604928   83  Linux
/dev/sda2   *        2566        6687    33104896    7  HPFS/NTFS
/dev/sda3            6687       60802   434673665    5  Extended
/dev/sda5            6687        7962    10240000   83  Linux
/dev/sda6            7962       60802   424432640    7  HPFS/NTFS

Disk /dev/dm-0: 33.9 GB, 33899413504 bytes
255 heads, 63 sectors/track, 4121 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7e7001c0

Disk /dev/dm-0 doesn't contain a valid partition table

```

---

### Post by peacebreaker on 2011-05-16
Anything at all?

---

### Post by drs305 on 2011-05-16
Are you selecting Windows from the Grub menu and *then* as Windows boots you are getting the blinking cursor? 

Or is it booting to the cursor without you selecting anything.

If the second one, it sounds like a common problem in Natty having to do with Grub/kernel video issues. Take a look at this thread by forum member *MAFoElffen*:
[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")
That thread is the best place to go for problems with a **Natty** video problem. 

Otherwise, please click on the "BIS-2" link in my signature line. It will download a boot info script. Run the boot info script, then post the contents of RESULTS.txt. 

When you are ready to copy the contents, click on the # icon in the post's menubar. This will generate [noparse]```
 
``` [/noparse] tags. Paste between them. It helps with formatting.

RESULTS.txt will show the status of your boot files and allow us to make informed suggestions. If you have trouble running it you can view the instructions by clicking the "BIS" link. There are additional instructions by *louieb* on that page on the left side.

---

### Post by peacebreaker on 2011-05-16
Ah nevermind... i was waiting too long with no answer, reinstalled the windows and then reinstalled the ubuntu. Take much longer with nobody helps, but now grub2 can dual boot properly.

---

