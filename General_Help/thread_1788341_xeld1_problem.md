---
title: "xeld1 problem"
date: 2011-06-22
forum: General Help
---

### Post by DashMusic on 2011-06-22
Hi! I've got a problem. When I boot my computer and I press the Windows 7 (Loader) (on dev/sda1) or something like that, a black screen comes up saying:

no xeld1
 no xeld1
 no xeld1

BIOS: Drive=0x0, H=2, S=18

cannot find xeld1 in all drives. press crtl+alt+del to restart._

I have three partitions, one is ubuntu, other is the grub and the other is windows 7.  Please help me! If you need more data just ask for it.

---

### Post by sanderd17 on 2011-06-22
Did you do something special? e.g. update grub, resize partitions or is it just a brand new ubuntu installation?

In any case, can you run the boot info script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It's explained quite well how to run.

---

### Post by DashMusic on 2011-06-22
This is what boot info gave me:

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros, 625142448 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   327,677,804   327,677,742   7 NTFS / exFAT / HPFS
/dev/sda2         327,677,866   625,141,759   297,463,894   f W95 Extended (LBA)
/dev/sda5         327,677,868   522,721,279   195,043,412   b W95 FAT32
/dev/sda6         522,723,033   606,244,904    83,521,872  83 Linux
/dev/sda7         623,142,912   625,141,759     1,998,848  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        18681D3C681D19D8                       ntfs       
/dev/sda5        1F07-0FB2                              vfat       COMPARTIDO
/dev/sda6        fa058a3f-65ad-4408-a165-69c3cb9b686d   ext4       
/dev/sda7        634beae2-3883-40ec-9bbf-2f62811d0dd2   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/18681D3C681D19D8  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: línea 1888: (  / 2 ) + 16 : error sintáctico: se esperaba un operando (el elemento de error es "/ 2 ) + 16 ")

---

### Post by sanderd17 on 2011-06-22
I see nothing special. Can you use a windows repair disk to repair windows?

---

### Post by DashMusic on 2011-06-22
I don't have one, that's my problem. If you know, could you tell me where to download one? I've searched, but I couldn't find it.

---

### Post by sanderd17 on 2011-06-22
I guess you need to take a look on the manufacturers site, and if you don't find one, download an illegal one (which is not illegal since you have a license).

I'm sorry, but I don't have a Windows license any more (bought a computer without OS) so I can't really help you much further.

---

