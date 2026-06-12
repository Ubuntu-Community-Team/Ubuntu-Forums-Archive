---
title: "Thrown to grub rescue after messing around with ext2fsd"
date: 2010-11-16
forum: General Help
---

### Post by Tryfon on 2010-11-16
Ok, I have a new Asus Eee Pc 1215n and installed on it Ubuntu 10.10. This way it was configured as dual-boot with 4 partitions. One for Windows7 one for Windows recovery, one for Linux swap and one ext4 for Ubuntu.
Everything was working fine until I installed the ext2fsd driver on Windows. It couldn't read the ext4 partition properly so I played with the options. There I tried changing the ext partition's type from "Linux" to "Linux extend" (which was obviously wrong). After the reboot I get a message when the computer starts up saying "error: partition not found" and in the next line "grub rescue>" with a dash flashing but without any recognizable commands.
I tried reinstalling grub from the Ubuntu 10.10 live cd following these instructions but now I get exactly the same screen, this time saying "error: file not found." instead. What was weird was that gparted in the live Ubuntu couldn't see any partition in the hard drive. It appeared like the whole space was unallocated.
When I type 'help' in "grub rescue" it tells me "unknown command". 
When I type 'ls' it returns: (hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)
I think this might be a clue of what is going on since all the partitions should not be flagged as msdos.

Help please! I don't want to reinstall everything!

---

### Post by psusi on 2010-11-16
You need to fire up fdisk and fix the partition you broke, changing the type back to Linux instead of extended.

---

### Post by drs305 on 2010-11-16
> **Tryfon said:**
> 
When I type 'ls' it returns: (hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)
I think this might be a clue of what is going on since all the partitions should not be flagged as msdos.

Help please! I don't want to reinstall everything!

The "msdos" designation is correct. You will notice that there is no (hd0,msdos4). As *psusi* states, you are going to have to try to restore the partition table to get the system to see sda4 again. Until you do, Grub2 isn't going to find your boot files.

---

### Post by Tryfon on 2010-11-16
Thanks a lot for the reply but I have no idea how to use fdisk. Any clues to get me started?

---

### Post by psusi on 2010-11-16
sudo fdisk /dev/sda

p prints the table
t tags a partition
w writes the changes and exits

You need to change the tag back to Linux instead of Extended.

---

### Post by Tryfon on 2010-11-16
Ok, I fixed the partition table and now gparted inside the live Ubuntu system does see all partitions. sda4 is shown as unallocated. I try the command "sudo fdisk /dev/sda4" to change the partition type to "Linux" again but I get the message "Unable to read /dev/sda4". It looks like the partition is screwed and I'll have to reformat it. Any last suggestions before formatting?

---

### Post by drs305 on 2010-11-16
> **Tryfon said:**
>  Any last suggestions before formatting?

Yes, try testdisk to restore it.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status")

---

### Post by psusi on 2010-11-16
It's just sudo fdisk /dev/sda... no 4.

---

### Post by Tryfon on 2010-11-16
Ok, I've tried everything but the Linux partition is dead. I'll have to reinstall. At least I didn't loose the windows installation!

Thank you everybody for your help!

I'll mark the thread as solved.

---

