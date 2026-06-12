---
title: "Changing NTFS mounted disk names."
date: 2010-04-29
forum: General Help
---

### Post by gencon on 2010-04-29
Using: Kubuntu/Karmic (but I'm guessing this applies to Ubuntu, Kubuntu, and all variants).

My PC has 3 SATA hard disks inside it, because it used to be a dedicated Windows XP machine NTFS is the file system on my non-Linux partitions. The disks are set up as follows.

Disk A: Windows OS Partition NTFS 100 GB
Disk A: Kubuntu / (Root) Partition EXT3 50 GB
Disk A: Kubuntu SWAP Partition 8 GB
Disk A: Kubuntu /home Partition EXT3 300 GB

Disk B: NTFS 500 GB

Disk C: NTFS 1000 GB

So there are 3 Windows XP in origin NTFS file systems that I access from Kubuntu, the Windows OS partition on Disk A, and the 2 other disks B and C.

In the Dolphin file manager these disks are automatically mounted and given names.

Disk A Windows OS Partition = 'Volume (ntfs)'
Disk B = 'Local Disk'
Disk C = 'Local Disk'

When selecting a file in an application which uses a 'drop down' style file selector, the 2 'Local Disk' names are distinguished from each other by the addition of a '1', so the 2nd 'Local Disk' becomes 'Local Disk1'.

Clearly these names are not very good. I would like to change them as follows:

Disk A Windows OS Partition = 'Volume (ntfs)' = 'WinOS'
Disk B = 'Local Disk' = 'Work'
Disk C = 'Local Disk' = 'Media'

How do I go about doing this in my Kubuntu setup?

Thanks all.

---

### Post by Morbius1 on 2010-04-29
The safest way is to log into your Windows OS and change them from windows.

Second safest way is to install and use gparted. You will have to unmount the NTFS drives before you change their labels if you're doing it using gparted.

---

### Post by gencon on 2010-04-29
> **Morbius1 said:**
> The safest way is to log into your Windows OS and change them from windows.
Thanks for your reply Morbius1.

The Windows alteration sounds the best way for me, I don't fancy the gparted option.

No problem I'm sure with the 2 'Local Disk' names, but what about the Windows OS Partition currently called 'Volume (ntfs)'? That is my Windows C drive and it is not called 'Volume (ntfs)' in Windows!

I am surprised there is no easy way of editing wherever the mount commands get done on login and specifying a name there.

---

### Post by scouser73 on 2010-04-29
Follow the instructions here to change the drive names: [[COLOR="Red"]**Rename USB Drives**[/COLOR]]("https://help.ubuntu.com/community/RenameUSBDrive")

---

### Post by gencon on 2010-04-29
> **scouser73 said:**
> Follow the instructions here to change the drive names: [[COLOR=Red]**Rename USB Drives**[/COLOR]]("https://help.ubuntu.com/community/RenameUSBDrive")
Thanks scouser.

The instructions are clear and helpful. However I am a little worried that the instructions page is called: **RenameUSBDrive**.

My drives are internal SATA disks and do not use USB.

Should I be worried or are the instructions for internal drive partitions (which I must say they appear to be)?

Thanks.

---

