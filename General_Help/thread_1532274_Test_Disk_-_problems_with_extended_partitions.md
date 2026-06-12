---
title: "Test Disk - problems with extended partitions"
date: 2010-07-16
forum: General Help
---

### Post by julkwiec on 2010-07-16
Hi. Something bad happened to my partition table, so right now I'm working from a Live CD. My partition table is completely screwed, although the data on the lost partitions hasn't been overwritten. I've been messing around with TestDisk for about an hour, but I still didn't figure out how to fix my problem.
Before the crash, I had 5 partitions:
NTFS - 30GB
NTFS -  8GB
ext4 - 20GB
and here comes the extended partition:
linux swap - 8 GB
NTFS - 400GB

TestDisk can see all those five partitions. I can mark swap as Logical, but I can't do so with the 400GB NTFS partition - there is just no selection. Turning on "expert mode" didn't help. I have read about using sfdisk to fix partition table, but I don't think I'm able to do it by myself. I would really appreciate your help :)



Here's how it looks in TestDisk:

```
Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  3915 254 63   62910477
D HPFS - NTFS           3916   0  1  4959 254 63   16771860 [Windows XP]
D Linux                 4960   0  1  7539 254 63   41447700
L Linux Swap            7540   1  1  8583 254 63   16771797
D HPFS - NTFS           8584   0  1 60800 254 63  838866105 [Reszta]
```



and, here is my slightly modified sfdisk table dump:


```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=         63, size= 62910477,  Id= 7
/dev/sda2 : start=   62910540, size= 16771860,  Id= 7
/dev/sda3 : start=   79682400, size= 41447700,  Id=83
/dev/sda4 : start=          0, size=         ,  Id= 5   //extended partition
/dev/sda5 : start= 	     , size= 16771797, Id=82	//8gb swap
/dev/sda6 : start=           , size= 838866105, Id= 7   //400gb ntfs
```


I've filled sizes according to TestDisk's findings. First 3 partitions were OK, the problem
lies in the extended partition holding 2 logical ones.

---

### Post by dcstar on 2010-07-16
> **julkwiec said:**
> 
.........
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=         63, size= 62910477,  Id= 7
/dev/sda2 : start=   62910540, size= 16771860,  Id= 7
/dev/sda3 : start=   79682400, size= 41447700,  Id=83
**/dev/sda4 : start=          0, size=         ,**  Id= 5   //extended partition
**/dev/sda5 : start= 	     ,** size= 16771797, Id=82	//8gb swap
**/dev/sda6 : start=           , **size= 838866105, Id= 7   //400gb ntfs
```


I've filled sizes according to TestDisk's findings. First 3 partitions were OK, the problem
lies in the extended partition holding 2 logical ones.

There is missing data in the table, here is one of mine as an example:
sfdisk -l
```
   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   1603    1604-  12884098+   7  HPFS/NTFS
/dev/sda2       1604    2622    1019    8185117+  83  Linux
/dev/sda3       2750    3642     893    7173022+  83  Linux
/dev/sda4       3825    4864    1040    8353800    5  Extended
/dev/sda5       4343    4864     522    4192965   82  Linux swap / Solaris
```
sfdisk -d
```
/dev/sda1 : start=       63, size= 25768197, Id= 7, bootable
/dev/sda2 : start= 25768260, size= 16370235, Id=83
/dev/sda3 : start= 44178750, size= 14346045, Id=83
/dev/sda4 : start= 61448625, size= 16707600, Id= 5
/dev/sda5 : start= 69770295, size=  8385930, Id=82
```

You should be able to figure out how yours should look.

---

