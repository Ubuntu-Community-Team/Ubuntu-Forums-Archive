---
title: "Cant change folder permissions on SD card."
date: 2011-02-09
forum: General Help
---

### Post by maxppp on 2011-02-09
I have a SD(SDHC 16gb) card plugged into my laptop. The whole thing is formatted as NTFS.

When i try to change folder permissions on the 'group' or 'other' attributes on the card using nautilus, it instantly switches them back to 'none' or '-----'.

Can anyone offer any insight? Hoping its not because its NTFS otherwise i imagine ill have to lose all the data if im to change the partiton type.

---

### Post by coffeecat on 2011-02-09
> **maxppp said:**
> Hoping its not because its NTFS

It's because it's NTFS. NTFS is a Microsoft filesystem and doesn't support the Linux/Unix system of ownership and permissions. Permissions are set globally by the mount options when mounting NTFS or FAT32, therefore you can't change permissions of individual files or folders.

Sorry.

---

### Post by maxppp on 2011-02-09
Thanks, at least i learned something!

Is there any other format i can partition it to (other than fat32) than will allow windows xp+ to be able to read it?

---

### Post by coffeecat on 2011-02-09
There are 3rd party Windows drivers for ext2/3, and I seem to remember reading about one for ext4. But they have to rely on workarounds for dealing with - you guessed it! - ownership and permissions. Personally, I wouldn't trust a Windows ext2 driver with valuable data, and I have no recent experience of them. 

Here is a rather bewildering chart for you: :)

[http://en.wikipedia.org/wiki/Comparison_of_file_systems#Supporting_operating_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Supporting_operating_systems)

---

