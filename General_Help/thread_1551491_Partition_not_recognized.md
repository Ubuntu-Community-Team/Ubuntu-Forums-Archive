---
title: "Partition not recognized"
date: 2010-08-12
forum: General Help
---

### Post by zulubk on 2010-08-12
My desktop has dual operating system.

I had totally four partitions

1. 1st Windows XP partition
2. 2nd Windows XP partition
3. Linux partition
4. Linux swap partition

I wanted to delete the Linux partition but accidentally deleted both Linux partition and Linux swap partition. 

After that when I tried to restart my machine the system automatically got me into GRUB.

I tried to repair the windows XP OS using the windows XP cd. I tried the repair option and it did not work. Instead of going through the normal validation....it staright way took me to C:. I tried chkdsk with possible options but it came back with one or more recoverable problems error.
Then I tried DIR to list folders, it came back with directory enumeration issue.
I tried to create a folder, it gave me the access denied issue.

Desperately I did the mistake of issuing FIXBOOT and FIXMBR in the C drive.

Then rebooted and found that the GRUb was no longer getting loaded.

I then came to know about testdisk and tried the package Ubuntu 10.4 live cd and loaded tesdisk and followed the steps. I was partially successfully in recreating the partition table. I was able to recover 1 windows partition, Linux partition and Linus Swap partition. Unfortunately the system is recognizing one full partition as free space.

I tried installing GRUB and now the machine is able to load GRUB on load
I recovered the data in the partition I recovered but still I am not able to figure out a way to fix the other partition. Any help will be really appreciated.

Thank you

---

