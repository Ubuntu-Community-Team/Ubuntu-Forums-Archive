---
title: "Clonezilla problem"
date: 2012-06-27
forum: General Help
---

### Post by olympic on 2012-06-27
I am having trouble attempting to make a copy of the 320GB hdd in my laptop using Clonezilla.  The hdd also uses BURG as a bootloader.

I have a dual boot sytem using Win7 and Ubuntu 12.04.

Configuration is as follows:

sda  -  sda1 - NTFS  Recovery       13.56GB
        sda2 - NTFS  SYS Reserved     100MB
        sda3 - NTFS                149.47GB
        sda4 - EXTENDED            135.02GB
        sda5 - EXT4  /              32.60GB
        sda6 - SWAP                  4.66GB
        sda7 - EXT4                 97.77GB

*_AFTER RUNNING CLONEZILLA_*

sdb  -  sdb1 - NTFS  Recovery       13.56GB
        sdb2 - NTFS  SYS Reserved     100MB
        sdb3 - NTFS                149.47GB
        sdb4 - EXTENDED            135.02GB
        **[COLOR="Red"]sdb5 - UNKNOWN FILESYSTEM[/COLOR]**
        sdb6 - SWAP                  4.66GB
        sdb7 - EXT4                 97.77GB

I then tried to just copy sda5 to sdb5 using the "dd" command.

The entry for sdb5 now reads  sdb5 - EXT4    32.60GB

But I am not able to use this drive as I get a "Grub Error" when that drive is installed in the computer.  All files etc in the Win7 and Ubuntu partitions however appear to have been copied.

Can anyone advise if the problem may be in the use of BURG as the bootloader, or if there may be another reason for the "/" partition not copying from sda5 to sdb5 in Clonezilla.

Also is it possible that "dd if=/dev/sda of=/dev/sdb bs=1024" may provide a bootable hdd, or should I revert to GRUB?

Any comments appreciated.

---

### Post by oscarivera9 on 2012-07-06
that's very interesting.
I don't know what it could be, but I'm wondering where your Ubuntu is installed.  Is it on your sda5 or sda7?  Both of those partitions are formatted to Ext. 4 so my guess is that one could be your /root and the other your /home, but I could be wrong.  Also, what makes you think that the problem is the Burg bootloader?  You could be correct in making that assumption but I don't see why that should mess with Clonezilla.

---

### Post by Mapel Jenny on 2012-07-06
To download the older versions, click on the Clonezilla live to the left of the version number.  You will get a list of all downloaded versions including the one I use below.

---

