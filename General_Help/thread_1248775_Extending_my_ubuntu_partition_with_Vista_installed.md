---
title: "Extending my ubuntu partition with Vista installed"
date: 2009-08-24
forum: General Help
---

### Post by traigo on 2009-08-24
I bought a dell with Vista pre-installed.  I installed Ubuntu on the 250g drive only allocating ~23g.  Now, I've been able to shrink my vista partition to 100g and I have 100g unallocated.  I don't know how to extend my partition into the new unallocated space.  I even tried just creating a new partition and moving /home there but it won't let me create more than 4 partitions.  I'm not really tied to vista, but I keep it around so I can play a few games randomly.  I can backup the games to my 1TB drive and reinstall vista if necessary.  I'd prefer not to have to reinstall ubuntu.  I've spent the last year getting used to it and configuring it the way I want.  Any help would be appreciated.  Also, should my swap be larger than 1gb?  I have 4gb RAM.

/dev/sda1 fat16 47.03mb
/dev/sda2 ntfs 10.00gb
/dev/sda3 ntfs 98.11gb
unallocated 102.12gb
/dev/sda4 extended 22.54gb
/dev/sda5 ext3 21.56gb
/dev/sda6 linux-swap 1004.03mb


Thanks,
Traigo

---

### Post by drs305 on 2009-08-24
The "Expand /" link in my signature line has some guidelines for expanding a system (/) partition. It's not exactly your case but the principles are the same.

A 1GB swap should be fine for normal users.

---

### Post by louieb on 2009-08-24
Using a live CD run Gparted. If your partitions are just like you listed then you grow extended partition sda4 to occupy the unallocated space. 

It will still be unallocated but then you will be able to grow sda5 to use the space. Or you can create a logical partition in the unallocated space (recommended). Don't bother to try and make it /home just use the new partition   for data, music, whatever.

If you choose to grow sda5 then you will need  to setup grub again. 
Even though the title is after windows install the same will work for you too. [Fix Grub after Win install - catlett]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")

---

### Post by traigo on 2009-08-26
Thanks for the help.  Using the live CD and gparted, I managed to expand sda4 to include the unallocated space and sda5 as well.  It took a bit to figure out since the live CD mounted the swap partition and I had to unmount it before I could continue.  After that, I just followed the Expand / screenshots from drs305.  I didn't have to setup grub again.

now:
/dev/sda1 fat16 47.03mb
/dev/sda2 ntfs 10.00gb
/dev/sda3 ntfs 98.11gb
/dev/sda4 extended 124.67gb
/dev/sda5 ext3 123.68gb
/dev/sda6 linux-swap 1004.03mb

---

