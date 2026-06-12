---
title: "Error: Can't have overlapping partitions"
date: 2010-04-24
forum: General Help
---

### Post by qvyang on 2010-04-24
I deleted my vista drive(to upgrade to win 7) but can't reformat it. And I got this error message when I try to format the unallocated disk: Can't have overlapping partitions.

This is what I get after I run sudo fdisk -l, sda2 is my ubuntu partition, sda5 is the swap partition.


```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    5  Extended
/dev/sda2             487        7781    58597087+  83  Linux
/dev/sda5               1         486     3903732   82  Linux swap / Solaris

```

Please help! I don't want to format my ubuntu's partition.

---

### Post by srs5694 on 2010-04-24
Something has damaged your partition table; your extended partition (/dev/sda1) covers the whole disk, but you've got a primary partition (/dev/sda2) that overlaps its area. (/dev/sda5 is a logical partition, which resides inside the extended partition, so it's OK.)

Your existing configuration is actually quite ugly. It may be possible to salvage it with sfdisk, but I'm not very experienced with the specific operations you'd need, so I'll offer another (albeit provisional) suggestion: *If* you don't want to re-install Windows on the disk, you could convert it to GPT pretty easily, using [GPT fdisk.](http://sourceforge.net/projects/gptfdisk/files/) Download whichever .deb file is appropriate for your CPU and install it. This will give you program files called gdisk and sgdisk. Type "sudo gdisk /dev/sda", type "p" to verify that your two Linux partitions (/dev/sda2 and /dev/sda5) exist, and then type "w" to save your partitions in GPT form. (You can also create new partitions, if you like.) If you don't see your two partitions when you type "p", type "q" to quit rather than "w" to write your changes to disk! Assuming a successful conversion, you'll then need to re-install your boot loader. Typing "sudo grub-install /dev/sda" should do the trick.

This procedure isn't without risk; there's a chance that you'll have to debug boot problems, and a much slimmer chance that your partitions will be seriously damaged. Backing up beforehand is therefore advisable. GPT has the advantage of not using extended or logical partitions, so the ugly weirdness that's somehow been created on your disk won't be an issue.

---

### Post by qvyang on 2010-04-24
Thanks for your reply! This is what I got:

```
Command (? for help): p
Disk /dev/sda: 488397168 sectors, 232.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 1B17FD84-51FC-42ED-9358-48FECE97B322
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 488397134
Partitions will be aligned on 2-sector boundaries
Total free space is 363395462 sectors (173.3 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   2         7807590       125001764   55.9 GiB    0700  Linux/Windows data
   5             126         7807589   3.7 GiB     8200  Linux swap

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed, possibly destroying your data? (Y/N): 

```

When I installed my ubuntu/vista dual boot I remember I had 4 partitions in total:
one for ubuntu 55.9GB
one Linux swap 3.7GB
one for vista (which i further partitioned to 2 logical partitions C: 54.4GB and D: 118GB) 172.4GB
one for vista swap (can't remember how big)

So now if now I overwrite my existing partitions what happens the my other partitions? My final goal is to format my vista partition and install windows 7 on it.

---

### Post by qvyang on 2010-04-25
ok, I just overwrote my existing partitions and now I can see the following partitions in gparted:

/dev/sda5 linux-swap  size: 3.72GB
/dev/sda2 ex3 size: 55.88GB
unallocated size: 173.28GB

The problem now is that the unallocated partition is in GPT format. I can't format it into NTFS for windows. How can I do that?

---

### Post by srs5694 on 2010-04-25
I'm afraid you missed a highly critical point in my earlier post:

> **srs5694 said:**
> *If* you don't want to re-install Windows on the disk, you could convert it to GPT pretty easily

Note the word "if," which was italicized in the original. Since you want to re-install Windows, converting to GPT may not have been the best choice, since Windows can't boot from GPT disks on BIOS-based computers. Still, it can be salvaged, in one of three ways:


[LIST]
[*]If your computer has an EFI or UEFI option, you can enable that option to enable Windows to install to GPT. You'll then need to adjust your Ubuntu boot options, but I'm afraid I don't know much about booting Linux on an EFI/UEFI-based system.
[*]You can keep the GPT configuration, but add a [hybrid MBR]("http://www.rodsbooks.com/gdisk/hybrid.html") to make Windows happy.
[*]You can convert the GPT back to MBR form by using the 'g' option on the GPT fdisk (gdisk) experts' menu. You'll also need to re-install GRUB (again).
[/LIST]


Each option has its advantages and disadvantages. Hybrid MBRs are flaky and dangerous, and if you use one Windows will be able to see a maximum of three partitions; but using a hybrid MBR will give you a lot of flexibility in terms of interspersing MBR primary partitions (for Windows' use) with GPT partitions (for use by Linux). Converting back to MBR will be safer, on the whole, but you'll need to deal with limitations of primary vs. logical partitions. For instance, all your logical partitions must be contiguous. Given that your Linux partitions are at the start of the disk, with very little free space before them, you'll need to put Windows immediately after Linux and then put any logical partitions (if any) after Windows.

Given your existing layout, I'd say that *if* you want to create just one partition for Windows, you're best off converting back to MBR. If, OTOH, you want to add additional partitions, and especially if you want to create more Linux partitions, it's more of a toss-up. To convert back to MBR, you'd do something like this (I've created something akin to your current configuration on a USB flash disk for demonstration):

```

$ sudo gdisk /dev/sdc
GPT fdisk (gdisk) version 0.6.6

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): r

Recovery/transformation command (? for help): p
Disk /dev/sdc: 31576064 sectors, 15.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 75C58B93-05BD-4879-B6C1-7A372E985E7C
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 31576030
Partitions will be aligned on 32-sector boundaries
Total free space is 7221276 sectors (3.4 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   2         7577632        24354847   8.0 GiB     0700  Linux/Windows data
   5              96         7577600   3.6 GiB     8200  Linux swap

Recovery/transformation command (? for help): g
Sorted GPT partitions and their current conversion status:
                                      Can Be
Number    Boot    Size       Status   Logical   Code   GPT Name
   1             3.6 GiB     primary     Y       82    Linux swap
   2             8.0 GiB     primary     Y       07    Linux/Windows data

Type partition to change, 0 to accept, -1 to abort: 2
What do you want to do?
 a - toggle active flag
 d - drop partition from MBR
 l - convert partition to logical
 t - change MBR type code
Action: t
Enter a 2-byte hexadecimal MBR type code: 83
Sorted GPT partitions and their current conversion status:
                                      Can Be
Number    Boot    Size       Status   Logical   Code   GPT Name
   1             3.6 GiB     primary     Y       82    Linux swap
   2             8.0 GiB     primary     Y       83    Linux/Windows data

Type partition to change, 0 to accept, -1 to abort: 0

Converted 2 partitions. Finalize and exit? (Y/N): y
GPT data structures destroyed! You may now partition the disk using fdisk or
other utilities.

```The main thing that requires noting is changing the partition type code for the Linux data partition; the GPT-to-MBR conversion defaults to converting it to type 0x07 (NTFS), but it should be 0x83 (Linux data). (This quirk is a consequence of the fact that Linux and Windows use the same partition type code in GPT, but different codes in MBR.) If you forget this, you can do it using fdisk after you complete the conversion.

[quote=qvyang]The problem now is that the unallocated partition is in GPT format. I  can't format it into NTFS for windows. How can I do that?     
[/quote]You don't have an unallocated partition; you have unallocated *space.* To create a filesystem, you must create a partition. In GParted, you should right-click the unallocated space and select New from the pop-up menu.

---

### Post by qvyang on 2010-04-25
Thanks for you reply! Now I run into a new problem. I can not install my GRUB properly.

```
victor@victor-laptop:~$ sudo gdisk /dev/sda
[sudo] password for victor: 
GPT fdisk (gdisk) version 0.6.6

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): ?
b	back up GPT data to a file
c	change a partition's name
d	delete a partition
i	show detailed information on a partition
l	list known partition types
n	add a new partition
o	create a new empty GUID partition table (GPT)
p	print the partition table
q	quit without saving changes
r	recovery and transformation options (experts only)
s	sort partitions
t	change a partition's type code
v	verify disk
w	write table to disk and exit
x	extra functionality (experts only)
?	print this menu

Command (? for help): r

Recovery/transformation command (? for help): ?
b	use backup GPT header (rebuilding main)
c	load backup partition table from disk (rebuilding main)
d	use main GPT header (rebuilding backup)
e	load main partition table from disk (rebuilding backup)
f	load MBR and build fresh GPT from it
g	convert GPT into MBR and exit
h	make hybrid MBR
i	show detailed information on a partition
l	load partition data from a backup file
m	return to main menu
o	print protective MBR data
p	print the partition table
q	quit without saving changes
t	transform BSD disklabel partition
v	verify disk
w	write table to disk and exit
x	extra functionality (experts only)
?	print this menu

Recovery/transformation command (? for help): g
Sorted GPT partitions and their current conversion status:
                                      Can Be
Number    Boot    Size       Status   Logical   Code   GPT Name
   1             3.7 GiB     primary     Y       82    Linux swap
   2             55.9 GiB    primary     -       07    Linux/Windows data
   3             173.3 GiB   primary     -       07    Linux/Windows data

Type partition to change, 0 to accept, -1 to abort: 3
What do you want to do?
 a - toggle active flag
 d - drop partition from MBR
 l - convert partition to logical
 t - change MBR type code
Action: 83
Unrecognized command; making no change.
Sorted GPT partitions and their current conversion status:
                                      Can Be
Number    Boot    Size       Status   Logical   Code   GPT Name
   1             3.7 GiB     primary     Y       82    Linux swap
   2             55.9 GiB    primary     -       07    Linux/Windows data
   3             173.3 GiB   primary     -       07    Linux/Windows data

Type partition to change, 0 to accept, -1 to abort: 3
What do you want to do?
 a - toggle active flag
 d - drop partition from MBR
 l - convert partition to logical
 t - change MBR type code
Action: t
Enter a 2-byte hexadecimal MBR type code: 83
Sorted GPT partitions and their current conversion status:
                                      Can Be
Number    Boot    Size       Status   Logical   Code   GPT Name
   1             3.7 GiB     primary     Y       82    Linux swap
   2             55.9 GiB    primary     -       07    Linux/Windows data
   3             173.3 GiB   primary     -       83    Linux/Windows data

Type partition to change, 0 to accept, -1 to abort: 0

Converted 3 partitions. Finalize and exit? (Y/N): y
Warning: The kernel is still using the old partition table.
The new table will be used at the next reboot.
GPT data structures destroyed! You may now partition the disk using fdisk or
other utilities.
victor@victor-laptop:~$ sudo grub-install /dev/sda
Searching for GRUB installation directory ... found: /boot/grub
The file /boot/grub/stage1 not read correctly.
```

I also tried this:
```
victor@victor-laptop:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub> root (hd0,0)
root (hd0,0)
grub> setup (hd0)
setup (hd0)

Error 17: Cannot mount selected partition

```

When I use gdisk to convert MBR back to GPT the grub install had no problem at all. Now I'm stuck. I search though many forums but can't find any solution that solves my problem. :(

---

### Post by srs5694 on 2010-04-26
I think what's happened is that your partition numbers have changed, which means that your booted system doesn't match what GRUB is seeing. I'm afraid the only solution is to reboot using an emergency disc and install from that. Your Ubuntu install CD will probably do the job, but I don't happen to have step-by-step instructions for you.

Also, I think you changed the wrong partition type code; if I'm not mistaken, your new /dev/sda2 is your Linux installation, and it should be type 0x83, but you've left it at 0x07; and your new /dev/sda3 will eventually be your Windows system and so should be type 0x07, but you've changed it to 0x83. You'll need to use the 't' option in fdisk to change these type codes, then save the changes with 'w'. I'd do this before rebooting to your emergency system.

---

