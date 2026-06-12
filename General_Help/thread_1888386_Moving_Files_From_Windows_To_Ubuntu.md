---
title: "Moving Files From Windows To Ubuntu"
date: 2011-11-29
forum: General Help
---

### Post by shirbal on 2011-11-29
Hi all,

I am using windows and Ubuntu on the same laptop
first i had windows 7 and than i installed Ubuntu
how can i access my windows files (documents pictures and more) from Ubuntu
and how can i access my Ubuntu file from windows (if possible at all)

i am using windows 7 32bit and the latest version of Ubuntu

thanks all

shiran

---

### Post by Bogwitch on 2011-11-29
Hi Shirbal,

You should be able to mount your Windows partition directly under Linux. In fact, it should show up in the standard file browser, Nautilus. If it doesn't, you should be able to find the partition listed if you issue:
cat /proc/partitions
from a terminal, it should show you what partitions are on the HDD
if you issue:
df
from a terminal, you should see what partitions are mounted (or you could use mount to get the same info)
You should be able to mount the partition where your windows is installed using the command:
mount -t ntfs /dev/sda1 /mnt
Replace /dev/sda1 with the directory where your windows resides and /mnt with the directory you would like to mount the drive on.

As for accessing Linux partitions from Windows, you could try: [http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

I have not personally tried the software!

Bog

---

### Post by roger_1960 on 2011-11-29
Hi

If you have a dual boot installation where you choose which OS you start each time:

Ubuntu can see windows files, but probably not the other way.  In Ubuntu open nautilus (file manager), select from the menu VIEW > sidebar > places.  You should see at the top left under "devices" a drive listed.  Click on this to open (or mount and open) the drive which will likely be your windows partition.  You may see more depending on how your disk is partitioned.  You can then use file manager to handle these files.  Be careful not to mess up your windows installation!

Windows probably cannot read the ubuntu partition because it will be in ext3 or ext4 format which windows cannot handle.

---

### Post by BC59 on 2011-11-29
> **Bogwitch said:**
> 
As for accessing Linux partitions from Windows, you could try: [http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)



I tried to do it and it's not so easy. It's very very difficult to have full access to your Linux partitions.

---

### Post by shirbal on 2011-11-29
HI 

after running cat /proc/partition

i got:

major minor  #blocks  name

   7        0   30457856 loop0
   8        0  244198584 sda
   8        1    1536000 sda1
   8        2  232420348 sda2
   8        3   10240000 sda3


my files on windows is at my windows desktop

what now? i am not sure i understand

thank you

---

### Post by Bogwitch on 2011-11-29
> **BC59 said:**
> I tried to do it and it's not so easy. It's very very difficult to have full access to your Linux partitions.

By full, do you mean write?

The software claims to be read-only, ISTR from the dim and distant past that I had a utility (more specifically a driver) that allowed write on EXT2 but not on 3 or 4. As with many of these things, I have no recollection of the name or source of the software. :(

---

### Post by roger_1960 on 2011-11-29
Hi Shirbal

Try what I said in nautilus file manager - click the home folder icon in launcher to open it.

---

### Post by shirbal on 2011-11-29
hi 
in the devices i dont have nothing which is related to windows only the buckup partition for my windows

---

### Post by Bogwitch on 2011-11-29
> **shirbal said:**
> HI 

after running cat /proc/partition

i got:

major minor  #blocks  name

   7        0   30457856 loop0
   8        0  244198584 sda
   8        1    1536000 sda1
   8        2  232420348 sda2
   8        3   10240000 sda3


my files on windows is at my windows desktop

what now? i am not sure i understand

thank you

I'll have to assume that your Windows partition is the larger on, therefore the command to run will be:

mount -t ntfs /dev/sda2 /mnt

This should mount your windows drive on /mnt

It might be worth looking in /media, which is where windows partitions usually (I think) get mounted to see if it's there already.

HTH,

Bog

---

### Post by shirbal on 2011-11-29
hi all


i founde it under /host

thank u alll


shiran

---

### Post by Mark Phelps on 2011-11-29
> **shirbal said:**
> i founde it under /host
Which means ... you installed using Wubi.  Need to tell folks this, as since they didn't notice. You could end up trashing your install if you start installing GRUB -- or making other such changes.

---

### Post by shirbal on 2011-11-29
i am still new at ubuntu, what is the difference between Wubi and GRUB??

---

