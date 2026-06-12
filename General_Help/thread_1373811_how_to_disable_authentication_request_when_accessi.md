---
title: "how to disable authentication request when accessing another drive"
date: 2010-01-06
forum: General Help
---

### Post by yurib on 2010-01-06
hello,

I'm dual booting Ubuntu 9.10 and win7.
I have an NTFS partition on my disk and whenever i want to browse files on that partition I'm required to enter my password.
my problem is that my music folder is located on that partition, and as a result, whenever I open rhythmbox, it cant access the files on that partition and begins to remove them from the library. in order to prevent this i must browse to that partition manually and enter my password upon request, prior to opening rhythmbox.

i assume there's a simpler permanent solution...

thanks :)

on a side note - shouldn't the spell checker on the Ubuntu forums recognize "Ubuntu" as a legit word ? :P

---

### Post by John Bean on 2010-01-06
You can mount the NTFS volume at boot time. There are several ways to achieve this but this is probably the simplest for a non-technical user: [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

PS: the spellchecker is a part of your browser, nothing to do with the forum.

---

### Post by yurib on 2010-01-06
thanks a lot :)

---

### Post by Morbius1 on 2010-01-06
This is the old-school method if you're interested[I] :)

Step 1: Open a Terminal and type **sudo blkid**
[/I] 
You'll get an output that may include something like this:
> [COLOR=Blue]/dev/sda1[/COLOR]: UUID="DA9056C19056A3B3" LABEL="WinXP" TYPE="ntfs"*Step 2: Create a mount point for that partition to live in. For example:*

Open **Terminal**
Type [B]sudo mkdir [COLOR=DarkGreen]/media/WindowsXP[/COLOR]

[/B][I]Step 3: Add a line in /etc/fstab so that the partition will mount at boot to your mountpoint automatically and not prompt for a password:
[/I] 
[COLOR=Blue]/dev/sda1[/COLOR] [COLOR=DarkGreen]/media/WindowsXP[/COLOR] ntfs defaults,umask=007,uid=1000,gid=46 0 0

There are a hundred variations on that fstab entry but the one above will do the following:

umask=007 will enable read /write access to the owner and group
uid=1000 will make you the owner ( you need to verify if that's the right number for you by issuing the command: **id** in a terminal )
gid=46 will make the mount point accessable by group 46 (plugdev). All users on your box are members of plugdev.

---

