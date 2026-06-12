---
title: "Replacing Fedora 12 with UBUNTU 10.04"
date: 2010-05-27
forum: General Help
---

### Post by codingfreak on 2010-05-27
Hi

At present I got dual boot laptop with FEDORA 12 and Windows VISTA. Everything is going fine ... but now when I try to boot into FEDORA I am getting **NO ROOT DEVICE FOUND .. BOOT FAILED .. SLEEPING FOREVER**. Before that I installed proprietary Nvidia Drivers and it booted once successfully with proprietary drivers. Attempts to fix it using RESCUE MODE were fruitless and even raised a BUG and also a post in fedora forums.

Now I am looking for steps to replace FEDORA 12 with UBUNTU 10.04 without any pain .... I dont want my MS VISTA getting affected because of this .. :( sadly MS VISTA is more reliable until now than the Linux edition.

Guys any help or suggestions :)

---

### Post by PC_load_letter on 2010-05-28
I'm no expert, but here is what I'd do, I don't claim it's the safest or the best option, merely the only option I know of:

- First, I wouldn't erase the the Fedora 12 partition as it will erase grub and the mbr entry, and then for Windows to start, you'll need to fix the mbr (master boot record).

- So, I'd use the Ubuntu live CD (or from a USB drive) to shrink the Fedora 12 partition to its actual size. by this I mean if it has only 12 GB taken out of 20 GB, then you shrink it to 12GB. You do this using Gparted (from System > Administration). Make sure you back up all the important files on ALL the partitions, you'll never know what could go wrong. If asked for a password, it's an empty string, just hit enter. 
Although you can not start Fedora 12, the live Cd will give you access to the partition so that you can back up the important files. 

- Once you do this the available space that was freed becomes actual free space (unallocated) on the drive. Double check that it is the case w/ Gparted. 

- Now you can install Ubuntu using the option that lets it use the biggest chunk of unallocated (free) space on the disc. Hopefully Ubuntu will see both the installed systems. 

- Once Ubuntu is installed and you have no problems with it, you can go from Ubuntu and format the Fedora 12 partition, using Gparted again. 

As I said, I am not aware of any easier procedure. Maybe someone else can chime in w/ a better solution.

---

### Post by PC_load_letter on 2010-05-28
Or, of course, you could install Ubuntu from within Windows using the WUBI install from the live CD. Just run the live cd from Windows and run the wubi.exe, follow the instructions.

---

### Post by codingfreak on 2010-06-03
> **PC_load_letter said:**
> Or, of course, you could install Ubuntu from within Windows using the WUBI install from the live CD. Just run the live cd from Windows and run the wubi.exe, follow the instructions.

I am not much intrested in WUBI ... 

Hmm I am also worried .. if I try to install ubuntu it might replace GRUB as a result WINDOWS might not boot up ...

But if I can get the entry for the WINDOWS partition in FEDORA 12 grub.conf file then will I be able to boot Windows Partition ???

Even I heard that While installing Ubuntu will recognise the Windows Install and automatically include WINDOWS as part of new GRUB ... :) is that TRUE ??

---

### Post by codingfreak on 2010-06-26
WoW ... I have simply installed replacing the previous partitions of FEDORA 12 and once after installation I got a a DUAL boot option with VISTA and UBUNTU 10.04 ...

Thats really simply than I expected .......

---

### Post by coventry1966 on 2010-08-27
> **codingfreak said:**
> WoW ... I have simply installed replacing the previous partitions of FEDORA 12 and once after installation I got a a DUAL boot option with VISTA and UBUNTU 10.04 ...

Thats really simply than I expected .......

Codingfreak

Can you explain a little more as to how you did this. I'm in the same situation dual boot Vista and Fedora 12.

I want to replace the Fedora 12 with Ubuntu.

---

