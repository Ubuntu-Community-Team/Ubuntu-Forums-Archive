---
title: "Expand ext2 partition"
date: 2010-09-17
forum: General Help
---

### Post by jpcanaverde on 2010-09-17
Hi. I had an HFS+ partition with 30Gb, and a FAT32 7Gb parition. 

I didn't use both, so with GParted, I deleted them, but the blank spaces were separated (both "partitions" are logical partitions, in the same extended partition)

So I created a ext2 partition, in hope that I could expand it, but no luck.

Here's GParted Screenshot (I didn't actually deleted the FAT32 paritition just yet):

[img]http://img816.imageshack.us/img816/4794/screenshot5p.png[/img]

The partition I want to extend is sda8, using the free space of the sda7 I'm going to delete.

GParted just can't find the free space, so it doesn't let me expand, just shrink... Can you help me, please? Probably just missing something obvious...

Thanks,

JPCanaverde

---

### Post by plucky on 2010-09-17
1) You will have to turn off swap. 
2) Then delete swap and the fat32 partition.
3) Expand the sda8 partition but leave enough un-allocated space for swap.
4) Recreate the swap partition at the end of the extended partition.

The UUID for swap will change so you will have to edit the /etc/fstab and put in the new UUID so that they will mount.

Good luck

---

### Post by jpcanaverde on 2010-09-17
I didn't get it... The ext4 partition is my Ubuntu partition, it is associated with the swap... Isn't the swap necessary for Ubuntu to work? Or, if I recreate it, don't I have to do something else too?

Please explain step-by-step... Really hard to me like that...

Thanks.

---

### Post by plucky on 2010-09-17
> **jpcanaverde said:**
> I didn't get it... The ext4 partition is my Ubuntu partition, it is associated with the swap... Isn't the swap necessary for Ubuntu to work? Or, if I recreate it, don't I have to do something else too?

Please explain step-by-step... Really hard to me like that...

Thanks.

**You have to boot the Live Cd and run gparted from there.**

Your system should be able to run without a swap partition.Think of it as a safety net for when you need extra memory.It will only get used when you fill up physical memory.

Boot the Live CD and make the changes.

When you reboot the main system,you should find that the swap partition will not mount as the UUID of the partition will have changed.

To get the new UUID use the command ```
sudo blkid
``` in a terminal.

To edit the /etc/fstab file use ```
gksudo gedit /etc/fstab
``` and copy and paste the uuid displayed in the first command into the the line for the swap partition in the /etc/fstab file

For instance my /etc/fstab looks like ```
 # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=83c63616-27f0-4cca-9c90-af716de57e94 /               ext4    errors=remount-ro 0       1
# /Storage was on /dev/sda6 during installation
UUID=a0fcecda-de1a-4892-b9a4-2b8c1ac374da /Storage        ext4    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=38265d9f-b40f-495b-96eb-85f30d32a430 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=[color=blue]acdc5e4a-4322-4a98-b9ac-4ae49aa82535[/color] none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

and my sudo blkid command looks like 
```

/dev/sda1: UUID="83c63616-27f0-4cca-9c90-af716de57e94" TYPE="ext4" 
/dev/sda5: UUID="38265d9f-b40f-495b-96eb-85f30d32a430" TYPE="ext4" 
/dev/sda6: UUID="a0fcecda-de1a-4892-b9a4-2b8c1ac374da" TYPE="ext4" 
/dev/sda7: UUID="[color=blue]acdc5e4a-4322-4a98-b9ac-4ae49aa82535[/color]" TYPE="swap" 

```


Good luck

---

