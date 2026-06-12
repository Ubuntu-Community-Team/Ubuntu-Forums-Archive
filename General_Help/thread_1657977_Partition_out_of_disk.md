---
title: "Partition out of disk"
date: 2011-01-01
forum: General Help
---

### Post by ZebaSz on 2011-01-01
There's a long story about how I got to the current problem, as I had a problem before with partitioning, but I guess the only important piece of information is I fixed it with testdisk.
Now, if I open Gparted, I see all my disk as unallocated. If I go the properties, I get an error about not being able to make a partition outside of the disk.
Here is what I get with "fdisk -l" (I apologize, the output is in spanish, though you most likely can understand the data):
```
Disco /dev/sda: 200.0 GB, 200049647616 bytes
255 cabezas, 63 sectores/pista, 24321 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x4ccc4ccb

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2           15666       21888    49985536   83  Linux
/dev/sda3           21889       24322    19551105    f  W95 Ext'd (LBA)
/dev/sda5           21889       24215    18683904   83  Linux

```
I did notice the end cylinder of the extended partition is 24322, while the HDD theoritacally has only 24321. Also, I remember having a swap partition inside of sda3.
Ubuntu works just fine, but I want to change my partitions without having to reinstall everything. Is this possible? Maybe there's a tool that could help me modify that faulty partition?

---

### Post by dcstar on 2011-01-02
> **ZebaSz said:**
> There's a long story about how I got to the current problem, as I had a problem before with partitioning, but I guess the only important piece of information is I fixed it with testdisk.
Now, if I open Gparted, I see all my disk as unallocated. If I go the properties, I get an error about not being able to make a partition outside of the disk.
Here is what I get with "fdisk -l"
......
[B]
gparted[/B] and **fdisk** use different methods to get the partition data, it seem you didn't "fix" things correctly. Try this:

[http://www.techrecipes.net/operatingsystem/linux/recover-lost-partition-table](http://www.techrecipes.net/operatingsystem/linux/recover-lost-partition-table)

---

### Post by Quackers on 2011-01-02
Compare the 2 items in red
```
Disco /dev/sda: 200.0 GB, 200049647616 bytes
255 cabezas, 63 sectores/pista, [COLOR="Red"]24321[/COLOR] cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x4ccc4ccb

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2           15666       21888    49985536   83  Linux
/dev/sda3           21889       [COLOR="Red"]24322[/COLOR]    19551105    f  W95 Ext'd (LBA)
/dev/sda5           21889       24215    18683904   83  Linux
```
[COLOR="Black"]Your extended partition has 1 sector more than the number of sectors on the hard drive. It needs to be reduced slightly.[/COLOR]

---

### Post by ZebaSz on 2011-01-02
> **dcstar said:**
> [B]
gparted[/B] and **fdisk** use different methods to get the partition data, it seem you didn't "fix" things correctly. Try this:

[http://www.techrecipes.net/operatingsystem/linux/recover-lost-partition-table](http://www.techrecipes.net/operatingsystem/linux/recover-lost-partition-table)
I already used testdisk before, and I still get a misformatted disk. I'll give gpart a try.
> **Quackers said:**
> Compare the 2 items in red
```
Disco /dev/sda: 200.0 GB, 200049647616 bytes
255 cabezas, 63 sectores/pista, [COLOR="Red"]24321[/COLOR] cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x4ccc4ccb

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2           15666       21888    49985536   83  Linux
/dev/sda3           21889       [COLOR="Red"]24322[/COLOR]    19551105    f  W95 Ext'd (LBA)
/dev/sda5           21889       24215    18683904   83  Linux
```
[COLOR="Black"]Your extended partition has 1 sector more than the number of sectors on the hard drive. It needs to be reduced slightly.[/COLOR]
That's exactly what I wanted, but I don't know how to do it. GParted (and Parted, the command-line one) can't even read the partition table properly.

---

### Post by oldfred on 2011-01-02
Drives are not defined by CHS but by LBA so you really need to run this as a cylinder may not be shown correctly.

```
sudo fdisk -lu
```

---

### Post by ZebaSz on 2011-01-04
fdisk -lu outputs this:
```
Disco /dev/sda: 200.0 GB, 200049647616 bytes
255 cabezas, 63 sectores/pista, 24321 cilindros, [COLOR="red"]390721968[/COLOR] sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x4ccc4ccb

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *          63    83891429    41945683+   7  HPFS/NTFS
/dev/sda2       251658240   351629311    49985536   83  Linux
/dev/sda3       351630720   [COLOR="Red"]390732929[/COLOR]    19551105    f  W95 Ext'd (LBA)
/dev/sda5       351631360   388999167    18683904   83  Linux

```
Yet again, sectors are not assigned properly.

---

### Post by coffeecat on 2011-01-04
Forum member srs5694 has written about this issue. Here is his webpage with the fix you need for this:

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by ZebaSz on 2011-01-04
You, sir, are amazing.
Thanks to everybody for your support. GParted is now happy, and so am I. Problem officially solved.

---

