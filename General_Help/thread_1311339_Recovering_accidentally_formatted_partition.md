---
title: "Recovering accidentally formatted partition"
date: 2009-11-02
forum: General Help
---

### Post by Suction Man on 2009-11-02
Major d'oh. I reinstalled Ubuntu, and forgot I hadn't kept /var on a separate partition, and consequently lost the MySQL databases I had sitting in /var/run/mysql. I reorganised the partitions at the time, and the blocks of the hard drive containing my /var (and the rest of the old Ubuntu filesystem) were replaced with a swap partition (perhaps sealing their fate).

As soon as I realised what I had done, I shutdown my fresh Ubuntu install and booted to LiveCD (with swap switched off). I used testdisk to make an image of the swap partition. After checking some old backups, it seems the .frm files MySQL uses for database table structure that are located in the directory /var/run/mysql/<dbname> have the opening bytes (in hex): FE 01 0A 09 03 00 00 10 01 00 00 30.

I ran a search for these using Scalpel, and it returned 134 matching strings of data (though cut short since my closing byte pattern is too ambiguous) - so I could well have access to 134 tables - I reckon that number could easily include all my lost tables.

I think my question ultimately addresses how the ext filesystem works. There's a possibility the swap partition hasn't been used at all, in which case the overwritten partition's filesystem index is still available (assuming ext keeps such an index at first few blocks of the partition). Or does it work differently?

Anyone have any advice or ideas I can try? I have the cloned image I got using testdisk ready and waiting. Many thanks!

---

### Post by Suction Man on 2009-11-02
Bump! I just need a short answer tbh - is there a software that can solve this for me or do I need to start figuring out more byte patterns? I've tried a couple of recovery programs (in Windows) and they just offer a GUI for what Scalpel and Foremost do.

---

### Post by P4man on 2009-11-02
I imagine you tried testdisk not only to clone the partition but also to recover the partition table and files on it? If not, that would probably be your best bet.

---

### Post by Suction Man on 2009-11-03
testdisk can find the partition, but I wasn't willing to restore the partition because I couldn't find out how testdisk actually goes about the job. It initially recognises all my partitions, but once I've ran a search, it shows only one of my existing partitions as well as the one I accidentally formatted. If I 'write changes to disk' are those two partitions all I'm going to have left on my drive? Or will it leave the other partitions unaffected where possible and simply restore those two partitions (I only want to restore one of them anyway..)

---

