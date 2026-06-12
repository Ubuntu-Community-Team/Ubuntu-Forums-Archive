---
title: "Write Zeros at end of drive"
date: 2011-10-10
forum: General Help
---

### Post by bakegoodz on 2011-10-10
I find it a waste of time the zero out a whole drive when I only need to wipe certain meta data, for instance boot loaders, GPT partitions and hardware and software RAID info. Wiping the first and last GB would be good enough for my needs. I can figure out how the syntax with dd or any dd variant to wipe the first GB, but I'm having trouble having it write at the end of the drive. The syntax I've tried, tries to read the end of /dev/zero too, which of coarse doesn't have an end. Anyone know a way to do this?

---

### Post by oldfred on 2011-10-10
I do not know your solution but have these suggestions.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)
or if bits of gpt left:
To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by bakegoodz on 2011-10-11
Yes I'm aware of these operations, a bit manual and tedious, especially frequency need to do this. Also, often it is difficult to know which of these operations I need to do on the pile of drives I have.

---

