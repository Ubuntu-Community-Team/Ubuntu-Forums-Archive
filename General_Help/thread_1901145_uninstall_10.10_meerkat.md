---
title: "uninstall 10.10 meerkat"
date: 2011-12-27
forum: General Help
---

### Post by Advait on 2011-12-27
Hi All,

I've got 10.10 installed dual boot on a client's WinXP laptop and I need to uninstall it. I found some uninstall instructions on the net (see below). Part of the instructions are

bootrec.exe /fixmbr
bootrec.exe /fixboot

Could someone confirm that this is the correct order or sequence for these commends? Just want to confirm to make sure I don't mess up the laptop. Thanks!

**********************
INSTRUCTIONS: On the other hand you might have installed Ubuntu on the other partition in dual boot mode. So now, if you delete or format the ubuntu partition then the windows boot-loader will no longer be available because when you installed Ubuntu it has replaced it with GRUB. So you won’t be able to boot into your Windows OS after deleting or formatting the Ubuntu partition.

step 1 : Insert the Windows 7/vista/xp DVD and restart your computer.

step 2 : Go to recovery windows/console and execute the following command(s) :

bootrec.exe /fixmbr
bootrec.exe /fixboot

to overwrite the MBR (Master Boot Record).

step 3 : Now, remove the installation disc, restart the computer and format ubuntu partition (ext3/4 file system) to a windows file system such as NTFS or FAT.

step 4 : That’s All. You are Done!
**********************

---

### Post by elliotn on 2011-12-27
for xp just boot with XP cd and go to command prompt and run fixboot or fixmbr

in win7 boot from cd and  all is easy there

---

### Post by elliotn on 2011-12-27
format the ubuntu partition first and restore windows bootloader

---

### Post by Advait on 2011-12-28
OK, now I'm confused. To remove 10.10 from the WinXP laptop, do I

1. Put in WinXP recovery CD, run fixboot  or fixmbr and then format the Ubuntu partition?

OR

2. Format the Ubuntu partition, put in the recovery CD and then run fixboot or fixmbr?

At the end of this process I want the Ubuntu partition reformatted and COMBINED (JOINED) with the Windows partition.

Thanks!

> **elliotn said:**
> format the ubuntu partition first and restore windows bootloader

---

### Post by elliotn on 2011-12-28
> **Advait said:**
> OK, now I'm confused. To remove 10.10 from the WinXP laptop, do I

1. Put in WinXP recovery CD, run fixboot  or fixmbr and then format the Ubuntu partition?

OR

2. Format the Ubuntu partition, put in the recovery CD and then run fixboot or fixmbr?

At the end of this process I want the Ubuntu partition reformatted and COMBINED (JOINED) with the Windows partition.

Thanks!

to format the ubuntu partition u must use the LiveCD, run gparted and format the ext partition to ntfs, Gparted can also join the partitions but you have to just delete and unallocate space.

it doesn't matter if u fix Windows boot first or before u format the ubuntu ext partition

---

### Post by Advait on 2012-01-01
OK, I got 10.10 successfully uninstalled from my client's laptop. I had to install the Recovery Console, fix the boot sector and then I used a 3rd party partition editor to get all the partitions merged into one. It was tricky but I finally got it all done. Thanks for your help!

The Ubuntu forum community is wonderful!

Cheers,

Advait

> **elliotn said:**
> to format the ubuntu partition u must use the LiveCD, run gparted and format the ext partition to ntfs, Gparted can also join the partitions but you have to just delete and unallocate space.

it doesn't matter if u fix Windows boot first or before u format the ubuntu ext partition

---

