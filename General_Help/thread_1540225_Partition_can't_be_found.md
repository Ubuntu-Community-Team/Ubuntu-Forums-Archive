---
title: "Partition can't be found"
date: 2010-07-27
forum: General Help
---

### Post by Martini Anderson on 2010-07-27
Recently I have been trying to get rid of the GRUB2 and decided to stick with only Windows for now, and happens that I've been able to fix the boot problem (thanks to the people here). Right now one of the partition I had can't be found, I have no idea why and how, using all the methods with Testdisk, still no luck, so I followed the instructions, analyzed the disk and this is what i get
```

Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  3977 254 63   63906507
P HPFS - NTFS           3978   0  1  5252 254 63   20482875
P HPFS - NTFS           5253   1  1 11789 254 63  105016842 [Entertainment]
D HPFS - NTFS          11789 254 63 18326 254 63  105016906

```
The last one i have no idea which one is, but I used to have an E drive called Files. When I try to change it to Primary it tells me that the structure is bad, if i ignore it, it wouldn't still change, tells me invalid structure
Before the quicksearch after Analyze, I can see a list like this:

```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  3977 254 63   63906507
 2 E extended              3978  20  9 19456 254 63  248668867
 3 P HPFS - NTFS           5253   1  1 11789 254 63  105016842 [Entertainment]
Space conflict between the following two partitions
 2 E extended              3978  20  9 19456 254 63  248668867
 3 P HPFS - NTFS           5253   1  1 11789 254 63  105016842 [Entertainment]
   X extended              3978  20 10  4099 145 14    1951745
 5 L Linux                 3978  20 11  4099 145 14    1951744
   X extended              4099 145 15  5252 229 33   18528256
 6 L Linux                 4099 177 47  5252 229 33   18526208
   X extended             11790   0  1 19456 254 63  123170355
 7 L HPFS - NTFS          11790   1  1 19456 254 63  123170292 [Files]

*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted

```7 is the partition i need to get back, but after analyzing i am not able to see it.. How do I recover that? I have been looking for the other helps and it just leads me to the same situation over and over, going in circles.

Thanks very much

---

