---
title: "Partition bigger than HDD size"
date: 2011-10-02
forum: General Help
---

### Post by capicoso on 2011-10-02
Hello. So yesterday i was going to uninstall my ubuntu and install a  clean and fresh xubuntu. Before uninstalling i ran the live-cd, tested  everything, etc, ran Gparted and checked the partitions, everything ok.  But i'm used to format with partition magic zzz... So i rebooted >  DOS > and ran magic. Then two messages appeared about two sectors  with errors i think... dont remember. So it "fixed" them. When i startup  partition magic i couldn't see the partitions, all the space was used  by " 108 error table"."Well partition magic is confused" i thought.. so  went to Gparted and it was screwed too. Showing all of my 465GB  unassigned, because my partitions are bigger than the disk size.
I  searched and i found people with the same problem, some with overexposed  partitions, and other problems. But they said Gparted caused the  problem... So i'm not 100% sure if i actually have the same problem
Anyways, here goes the info:

```
Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros, 976773168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0xce78ce78

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *          63   153597464    76798701    7  HPFS/NTFS
/dev/sda2       153597528   460792394   153597433+   7  HPFS/NTFS
/dev/sda3       460792458   931834259   235520901    7  HPFS/NTFS
/dev/sda4       931834260   976784129    22474935    f  W95 Ext'd (LBA)
/dev/sda5       931835904   933834735      999416   82  Linux swap / Solaris
/dev/sda6       933836800   934518783      340992   83  Linux
/dev/sda7       934520832   950142975     7811072   83  Linux
/dev/sda8       950145024   976771071    13313024   83  Linux
```

Note: cabezas=heads, sectores=sectors, cilindros=cylinders, comienzo=start, fin=end, bloques=blocks

the last partition ends at 976771071, thats still inside the disk

```
Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0xce78ce78

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        9561    76798701    7  HPFS/NTFS
/dev/sda2            9562       28683   153597433+   7  HPFS/NTFS
/dev/sda3           28684       58004   235520901    7  HPFS/NTFS
/dev/sda4           58005       60802    22474935    f  W95 Ext'd (LBA)
/dev/sda5           58005       58129      999416   82  Linux swap / Solaris
/dev/sda6           58129       58172      340992   83  Linux
/dev/sda7           58172       59144     7811072   83  Linux
/dev/sda8           59144       60802    13313024   83  Linux
```

Here,  the last partition ends outside the disk. That's why i'm confused, the  people with this problem had sectors outside the disk. My sectors look  normal.

So, i used testdisk:
```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  9560 254 63  153597402 [Win Coso]
 2 P HPFS - NTFS           9561   1  1 28682 254 63  307194867 [Win Audio]
 3 P HPFS - NTFS          28683   1  1 58003 254 63  471041802 [Datos Audio]
 4 E extended LBA         58004   0  1 60801 254 63   44949870
 5 L Linux Swap           58004  26  7 58128 133 37    1998832
   X extended             58128 165  1 58171  26 31     682069
 6 L Linux                58128 166 23 58171  26 31     681984
   X extended             58171  58  1 59143 169 34   15622207
 7 L Linux                58171  59  1 59143 169 34   15622144
   X extended             59143 201  1 60801  47 46   26626114
 8 L Linux                59143 202  4 60801  47 46   26626048




```

But everything looks normal to my eyes here... the partition ends at 60801 254 63 and the limit es 60801 255 63...
```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  9560 254 63  153597402 [Win Coso]
P HPFS - NTFS           9561   1  1 28682 254 63  307194867 [Win Audio]
P HPFS - NTFS          28683   1  1 58003 254 63  471041802 [Datos Audio]
L Linux Swap           58004  26  7 58128 133 37    1998832
L Linux                58128 166 23 58171  26 31     681984
L Linux                58171  59  1 59143 169 34   15622144
L Linux                59143 202  4 60801  47 46   26626048


```

As  you can see, i have 2 windows, adata partition and the rest is linux.  These 3 partitions are very important and have too much information.

The  problem seems to be at the end of the disk, so if i format the last  linux partition (/home) or even the four linux partitions, will it get  fixed?


Also, i saw a tutorial(in spanish) explaining how to solve something like this, but he had problems with sectors... 

Ps. i used palimptest and it says i got a partition with lots lots lots of TB unnasigned...


Thanks

---

### Post by jamesisin on 2011-10-02
I would attempt to remove all the superfluous partitions and begin your partitioning of those partitions again.  But I live dangerously.

---

### Post by capicoso on 2011-10-02
> **jamesisin said:**
> I would attempt to remove all the superfluous partitions and begin your partitioning of those partitions again.  But I live dangerously.

Yeah. I think i'm just going to format the last partition and see what happens...

---

### Post by capicoso on 2011-10-02
I should buy some glasses, there really was a bigger partition, many more sectors... I fixed it without having to format.
So if anyone interested, i'll post the solution. Maybe it'll help  someone in the future

Look at the original post to see how my partition table was.


Now i got this(fixed): 
```

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros, 976773168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0xce78ce78

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *          63   153597464    76798701    7  HPFS/NTFS
/dev/sda2       153597528   460792394   153597433+   7  HPFS/NTFS
/dev/sda3       460792458   931834259   235520901    7  HPFS/NTFS
/dev/sda4       931834260   976773167    22469454    f  W95 Ext'd (LBA)
/dev/sda5       931835904   933834735      999416   82  Linux swap / Solaris
/dev/sda6       933836800   934518783      340992   83  Linux
/dev/sda7       934520832   950142975     7811072   83  Linux
/dev/sda8       950145024   976771071    13313024   83  Linux
```How:

First make sure that its the same error: $ sudo parted print, if you get a message saying that the partition cant be bigger than the disk, then its the same

Run 
```
$ sudo fdisk -lu
```Now look at a partition that ends at a bigger number than the disk itself. In my case its /sda4

Now to fix the table run:

```
echo "start_sector,disk_total_sectors,id"  | sudo sfdisk -f -uS /dev/sda -N4 -O sda_sectors_modified.save
```start sector is the starting of the partition with the problem, again in my case: /sda4, id in my case is f
my line was like this:

```
echo "931834260,976773168,f"   | sudo sfdisk -f -uS /dev/sda -N4 -O sda_sectors_modified.save
```the sda_sectors_modified.save will be saved at /home, make a backup of it, if anything goes wrong you'll get the table back 

now it'll run and it'll show the old partition with the new one. Maybe the new one looks worse, like this:

```
ubuntu@ubuntu:~$ echo "931834260,976773168,f" | sudo sfdisk -f -uS /dev/sda -N4 -O sda_sectors_modified.save
Comprobando que nadie esté utilizando este disco en este momento...
Correcto

Disco /dev/sda: 60801 cilindros, 255 cabezas, 63 sectores/pista
Situación anterior:
Unidades = sectores de 512 bytes, contando desde 0

   Disp.  Inicio  Principio   Fin   Nº sect.  Id  Sistema
/dev/sda1   *        63 153597464  153597402   7  HPFS/NTFS
/dev/sda2     153597528 460792394  307194867   7  HPFS/NTFS
/dev/sda3     460792458 931834259  471041802   7  HPFS/NTFS
/dev/sda4     931834260 976784129   44949870   f  W95 Ext'd (LBA)
/dev/sda5     931835904 933834735    1998832  82  Linux swap / Solaris
/dev/sda6     933836800 934518783     681984  83  Linux
/dev/sda7     934520832 950142975   15622144  83  Linux
/dev/sda8     950145024 976771071   26626048  83  Linux
Atención: el tamaño dado (976773168) supera el tamaño máximo permitido (44938908)
Situación nueva:
Unidades = sectores de 512 bytes, contando desde 0

   Disp.  Inicio  Principio   Fin   Nº sect.  Id  Sistema
/dev/sda1   *        63 153597464  153597402   7  HPFS/NTFS
/dev/sda2     153597528 460792394  307194867   7  HPFS/NTFS
/dev/sda3     460792458 931834259  471041802   7  HPFS/NTFS
/dev/sda4     931834260 1908607427  976773168   f  W95 Ext'd (LBA)
/dev/sda5     931835904 933834735    1998832  82  Linux swap / Solaris
/dev/sda6     933836800 934518783     681984  83  Linux
/dev/sda7     934520832 950142975   15622144  83  Linux
/dev/sda8     950145024 976771071   26626048  83  Linux
Atención: la partición 4 finaliza más allá del final del disco
La nueva tabla de particiones se ha escrito correctamente

Volviendo a leer la tabla de particiones...

Si ha creado o modificado una partición DOS, como /dev/foo7, utilice dd(1)
para poner a cero los 512 primeros bytes: dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(Véase fdisk(8).)
```Note: situacion anterior= older situation. situacion nueva: newer situation
look at the end of /sda4 at the newer situation
And we get something about DOS
To fix it we have to write everything again, but replacing the total disk sectors with the number in () and that is **44938908**(in my case)**. **So it should look like this (in my case):

```
echo "931834260,44938908,f" | sudo sfdisk -f -uS /dev/sda -N4 -O sda_sectors_modified.save
```and now:

   ```
Disp.  Inicio  Principio   Fin   Nº sect.  Id  Sistema
/dev/sda1   *        63 153597464  153597402   7  HPFS/NTFS
/dev/sda2     153597528 460792394  307194867   7  HPFS/NTFS
/dev/sda3     460792458 931834259  471041802   7  HPFS/NTFS
/dev/sda4     931834260 1908607427  976773168   f  W95 Ext'd (LBA)
/dev/sda5     931835904 933834735    1998832  82  Linux swap / Solaris
/dev/sda6     933836800 934518783     681984  83  Linux
/dev/sda7     934520832 950142975   15622144  83  Linux
/dev/sda8     950145024 976771071   26626048  83  Linux
Situación nueva:
Unidades = sectores de 512 bytes, contando desde 0

   Disp.  Inicio  Principio   Fin   Nº sect.  Id  Sistema
/dev/sda1   *        63 153597464  153597402   7  HPFS/NTFS
/dev/sda2     153597528 460792394  307194867   7  HPFS/NTFS
/dev/sda3     460792458 931834259  471041802   7  HPFS/NTFS
/dev/sda4     931834260 976773167   44938908   f  W95 Ext'd (LBA)
/dev/sda5     931835904 933834735    1998832  82  Linux swap / Solaris
/dev/sda6     933836800 934518783     681984  83  Linux
/dev/sda7     934520832 950142975   15622144  83  Linux
/dev/sda8     950145024 976771071   26626048  83  Linux
```now it ends at 976773167. Yay! It REALLY is inside the disk now!

to make sure...

```
$sudo fdisk -lu
$sudo parted /dev/sda print
$sudo fsdisk -d
```So reboot and everything should be right now. At least it worked for me:P

Btw, i recommend to do it everything from a live-cd if possible

Hope it'll help someone!

---

