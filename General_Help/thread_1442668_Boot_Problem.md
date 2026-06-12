---
title: "Boot Problem"
date: 2010-03-30
forum: General Help
---

### Post by RadioMirchi on 2010-03-30
There is a severe problem in my system..

After i install Ubuntu (any version) it is not getting booted..

After the restart of first installation it is stopped at

"GRUB Loading..."

What is the problem..

to be more specific even Windows XP CD is not getting booted where as other versions of Windows are getting booted...

Only the Windows XP **_CD_** and **_Installed Ubuntu(any Linux)_** are not getting booted..

---

### Post by slinzex on 2010-03-30
I have boot problem too. In my case 

Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x3fbe44a5

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        3702    29736283+   7  HPFS/NTFS
/dev/sda2            3703       36150   260638560    7  HPFS/NTFS
/dev/sda3           36151       38913    22193797+   5  Extendida
/dev/sda5           36151       38792    21221833+  83  Linux
/dev/sda6           38793       38913      971901   82  Linux swap / Solaris

And I have ubuntu/winrows seven  

The problem is that when I restart  my computer, the grub start menu don't appears!!!!
I mean the menu for selecting OS. It starts windows seven by default.

I tried:
-super grub disk : all options.
-sudo grub .. find /boot or find grub ... all this >>>Error 15 file not found

I don't know what to do, so please help me

---

### Post by oldfred on 2010-03-30
slinzex, welcome to forums, but it is better (more polite to not steal someone else's thread) to start your own thread. Boot problems almost always are unique to configuration and commenting on two different one's in a thread is difficult.

RadioMirchi -So we can see your exact configuration. Please run this script.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by RadioMirchi on 2010-04-11
> **oldfred said:**
> 
So we can see your exact configuration. Please run this script.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.



```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb848b848

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    37,754,639    37,754,577   7 HPFS/NTFS
/dev/sda2          37,754,640   156,301,487   118,546,848   f W95 Ext d (LBA)
/dev/sda5          37,754,703    71,305,919    33,551,217   7 HPFS/NTFS
/dev/sda6          71,305,983   104,857,199    33,551,217   7 HPFS/NTFS
/dev/sda7         104,857,263   142,611,839    37,754,577   7 HPFS/NTFS
/dev/sda8         142,611,903   156,300,479    13,688,577   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        BEC87624C875DB5B                       ntfs                                     
/dev/sda5        D28C6B408C6B1E6B                       ntfs                                     
/dev/sda6        28009DF1009DC5EA                       ntfs                                     
/dev/sda7        4E14FD4814FD3415                       ntfs                                     
/dev/sda8        EA40C82140C7F1FD                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```


as i said you my windows xp cd and linux os are not booting..
i installed windows 2000 and upgraded to windows xp here..

---

### Post by oldfred on 2010-04-11
You system only shows XP in sda1. There is no win2000 nor linux installed.

---

### Post by RadioMirchi on 2010-04-11
> **oldfred said:**
> You system only shows XP in sda1. There is no win2000 nor linux installed.

yes ofcourse..
i first tried to install Windows XP.. but the CD(tried many) was not booting..

so installed ubuntu 9.04... but after installation during reboot it shows "GRUB Loading..." and stops there..

next i tried fedora.. same with it also..

so finally i installed Windows 2000, It installed well.. After installation kept the Windows XP CD i have and upgraded to XP through 2000..

so only Windows XP can be seen now..

---

