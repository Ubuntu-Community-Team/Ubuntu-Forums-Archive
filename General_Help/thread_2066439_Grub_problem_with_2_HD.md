---
title: "Grub problem with 2 HD"
date: 2012-10-04
forum: General Help
---

### Post by koCO78 on 2012-10-04
Hi! 

I'm having problems with Grub. I have 2 HD, the first with Xubuntu and a second one with Windows 7. 

This is a fidisk just to clarify. 

```
Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros, 976773168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 4096 bytes
Tamaño E/S (mínimo/óptimo): 4096 bytes / 4096 bytes
Identificador del disco: 0x000330e2

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *        2048   964407295   482202624   83  Linux
/dev/sda2       964409342   976771071     6180865    5  Extendida
La partición 2 no se inició en el limite físico del sector
/dev/sda5       964409344   976771071     6180864   82  Linux swap / Solaris

Disco /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros, 1953525168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 4096 bytes
Tamaño E/S (mínimo/óptimo): 4096 bytes / 4096 bytes
Identificador del disco: 0x00072b4a

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1            2048  1953521663   976759808    7  HPFS/NTFS/exFAT

AVISO: GPT (Tabla de partición GUID) detectado en '/dev/sdc'! La utilidad fdisk no soporta GPT. Use GNU Parted.


Disco /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros, 1953525168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x9a0fe1a4

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1            2048  1953521663   976759808    7  HPFS/NTFS/exFAT
```

But when I try to update grub to get windows option it just dont detect. 

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-31-generic
Found initrd image: /boot/initrd.img-3.2.0-31-generic
Found memtest86+ image: /boot/memtest86+.bin

```

How to fix grub?

---

