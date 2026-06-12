---
title: "gparted error: Can't have a partition outside the disk!"
date: 2011-02-27
forum: General Help
---

### Post by diegoocampo on 2011-02-27
Hi everyone, I think my partition table is messed up but i am not really able to fix it with my little knowledge about testdisk and fdisk. Would be really thankful if you guys can help me out!

This is what the command **fdisk -l -u** reports:

```


Disk /dev/sda: 500.1 GB, 500107862016 bytes                                                                                                                                         
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors                                                                                                               
Units = sectors of 1 * 512 = 512 bytes                                                                                                                                              
Sector size (logical/physical): 512 bytes / 512 bytes                                                                                                                               
I/O size (minimum/optimal): 512 bytes / 512 bytes                                                                                                                                   
Disk identifier: 0x00000000                                                                                                                                                         
                                                                                                                                                                                    
   Device Boot      Start         End      Blocks   Id  System                                                                                                                      
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS                                                                                                                   
Partition 1 does not end on cylinder boundary.                                                                                                                                      
/dev/sda2          409600   176216232    87903316+   7  HPFS/NTFS                                                                                                                   
/dev/sda3       176217111   234806038    29294464   83  Linux                                                                                                                       
/dev/sda4       234806040   976784129   370989045    f  W95 Ext'd (LBA)                                                                                                             
/dev/sda5       234806103   238709814     1951856   82  Linux swap / Solaris                                                                                                        
/dev/sda6       238709898   930163499   345726801    7  HPFS/NTFS                                                                                                                   
/dev/sda7       930163563   976559219    23197828+   7  HPFS/NTFS                                                                                                                   
/dev/sda8       976560128   976771119      105496    c  W95 FAT32 (LBA)   


```

Any ideas??

---

### Post by Habeouscorpus on 2011-02-27
I googled the "end on cylinder boundary" message, and I got this:

[http://www.linuxquestions.org/questions/ubuntu-63/how-to-fix-partition-not-end-on-cylinder-boundary-768635/](http://www.linuxquestions.org/questions/ubuntu-63/how-to-fix-partition-not-end-on-cylinder-boundary-768635/)

Apparently, that's nothing to worry about. 

The gparted error yielded this:

[http://ubuntuforums.org/archive/index.php/t-352723.html](http://ubuntuforums.org/archive/index.php/t-352723.html)

Be very careful, playing with partitions can be hazardous for your data. Back everything up if you can, so if it does go to heck, you can copy/paste!

---

### Post by Hedgehog1 on 2011-02-27
> **diegoocampo said:**
> 
This is what the command **fdisk -l -u** reports:

```

   Device Boot      Start         End      Blocks   Id  System                                                                                                                      
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS                                                                                                                   
Partition 1 does not end on cylinder boundary.                                                                                                                                      
/dev/sda2          409600   176216232    87903316+   7  HPFS/NTFS                                                                                                                   
/dev/sda3       176217111   234806038    29294464   83  Linux                                                                                                                       
[COLOR="YellowGreen"]**/dev/sda4       234806040   976784129   370989045    f  W95 Ext'd (LBA) **[/COLOR]                                                                                                            
[COLOR="Red"]->/dev/sda5       234806103   238709814     1951856   82  Linux swap / Solaris                                                                                                        
->/dev/sda6       238709898   930163499   345726801    7  HPFS/NTFS                                                                                                                   
->/dev/sda7       930163563   976559219    23197828+   7  HPFS/NTFS                                                                                                                   
->/dev/sda8       976560128   976771119      105496    c  W95 FAT32 (LBA)   
[/COLOR]

```


Habeouscorpus is quite correct that the 'does not end end on cylinder boundary' message is harmless.

Your drive is packed in an interesting way, but should work fine.

sda4 is a logical partition with 4 partitions in it ( sda5-sda8 )

Are your having Hard drive issues?  Or were you just curious?

:KS

---

### Post by srs5694 on 2011-02-28
Your partition table is corrupt. /dev/sda4 (an extended partition, not a logical partition as Hedgehog1 states) is too big for the disk -- note that its end sector number (976,784,129) is larger than the number of sectors on the disk [noparse](976,773,168).[/noparse] FWIW, TestDisk is one of the utilities that's known to create this problem. Although Linux seems to cope OK with this damage, most partitioning tools based on libparted (such as GParted and GNU Parted) don't; they usually report that the disk is entirely empty. [This Web page of mine]("http://www.rodsbooks.com/missing-parts/") describes this problem in more detail and provides solutions. Post back if you have more questions.

---

### Post by Hedgehog1 on 2011-02-28
> **srs5694 said:**
> ...note that its end sector number (976,784,129) is larger than the number of sectors on the disk [noparse](976,773,168).[/noparse]...

Good catch - I missed that.  Thanks!

:KS

---

### Post by diegoocampo on 2011-02-28
Thank you everyone for your help, 
I followed instructions in srs5694 webpage and I fixed it!, I had to use sfdisk command (the third option you gave). Now gparted recognize my partitions!

---

### Post by urustu on 2011-11-04
Hi everyone,

What is the url address of **srs5694's webpage**, please ?
I know the same problem as Diegoocampo, I have used TestDisk to recover a deleted partition by an abnormal screen refresh.


```
$ sudo fdisk -l -u /dev/sdb

Disque /dev/sdb: 500.1 Go, 500107862016 octets
255 têtes, 63 secteurs/piste, 60801 cylindres, total [COLOR=SeaGreen]**[COLOR=Black]9767[/COLOR]73168 **[/COLOR]secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0x71f12d3d

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sdb1            2048     8390655     4194304   83  Linux
[COLOR=DarkOrchid]**La partition 1 ne se termine pas sur une frontière de cylindre.**[/COLOR]
[SIZE=1]*[COLOR=DarkOrchid]Partition 1 does not end on cylinder boundary. [/COLOR]*[/SIZE]
/dev/sdb2         8392704    18878463     5242880   83  Linux
/dev/sdb3        18880512    60823551    20971520   83  Linux
**/dev/sdb4**        60838155   [COLOR=Red]**[COLOR=Black]9767[/COLOR]84129   **[/COLOR]457972987+   **5  Etendue**
/dev/sdb5        68839424    89810943    10485760   83  Linux
/dev/sdb6        96190464   125827071    14818304   83  Linux
...
...
/dev/sdb21      798515200   802707455     2096128   83  Linux
/dev/sdb22      802709504   813193215     5241856   83  Linux
/dev/sdb23      834166784   959995903    62914560   83  Linux
```

---

### Post by Quackers on 2011-11-04
It's here
[http://www.rodsbooks.com/missing-parts/](http://www.rodsbooks.com/missing-parts/)

---

### Post by urustu on 2011-11-04
Thank you. Congratulations to srs5694 for his tool FixParts.

---

### Post by Quackers on 2011-11-04
Indeed, it's a very useful little item :-)

---

