---
title: "Problem with access to firmware Rockchip MP4 USB"
date: 2011-01-01
forum: General Help
---

### Post by ttakun on 2011-01-01
I have a 16GB MP4 player bought in China. It's based on the Rockchip RK27 chipset.

I would like to access to the firmware through Linux, but I cannot access it.

When I connect the MP4 player to my laptop it's correctly mounted, but it seems as it has two partitions but only one is mounted and accessible

The MP4 can be seen mounted as /dev/sdb
```
~$ **mount**
/dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda4 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ttattakun/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ttattakun)
[COLOR="Red"]/dev/sdb on /media/684D-B64D type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)[/COLOR]

```

```
:~$ **lsusb**
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 062a:0000 Creative Labs Optical mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]Bus 001 Device 007: ID 071b:3203 Domain Technologies, Inc. [/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

And that's the final part from the **dmesg** command
```
[100168.112075] usb 1-5: reset high speed USB device using ehci_hcd and address 6
[100168.279916] usb 1-5: USB disconnect, address 6
[100365.728057] usb 1-5: new high speed USB device using ehci_hcd and address 7
[100365.861086] usb 1-5: configuration #1 chosen from 1 choice
[100365.863243] scsi5 : SCSI emulation for USB Mass Storage devices
[100365.863609] usb-storage: device found at 7
[100365.863615] usb-storage: waiting for device to settle before scanning
[100370.862000] usb-storage: device scan complete
[COLOR="Red"][100370.862475] scsi 5:0:0:0: Direct-Access     RockChip USBDISK  User    1.00 PQ: 0 ANSI: 0
[100370.862967] scsi 5:0:0:1: Direct-Access     RockChip USBDISK    SD    1.00 PQ: 0 ANSI: 0[/COLOR]
[100370.868715] sd 5:0:0:0: Attached scsi generic sg2 type 0
[100370.871357] sd 5:0:0:1: Attached scsi generic sg3 type 0
[100370.875689] sd 5:0:0:0: [sdb] 32278528 512-byte logical blocks: (16.5 GB/15.3 GiB)
[100370.875699] sd 5:0:0:0: [sdb] Assuming Write Enabled
[100370.875705] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[100370.880257] sd 5:0:0:0: [sdb] Assuming Write Enabled
[100370.880261] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[100370.880264]  sdb:
[100370.880739] sd 5:0:0:1: [sdc] Attached SCSI removable disk
[100370.884477] 
[100370.885413] sd 5:0:0:0: [sdb] Assuming Write Enabled
[100370.885417] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[100370.885421] sd 5:0:0:0: [sdb] Attached SCSI removable disk

```

I say that it is supposed to have two partitions, because when it's connected under Windows it takes two drive letters (one for the multimedia stuff and the other one it is not accessible either)

And in Linux in the File Explorer I can see what I assume are the two partitions (Rockchip USBDISK **SD** and Rockchip USBDISK **User**). But only the one labelled as **User** is mounted. And only that can be mounted/unmounted.

[[IMG]http://img341.imageshack.us/img341/4927/pantallazot.png[/IMG]](http://img341.imageshack.us/i/pantallazot.png/)

Any hints? 
Thank you in advance

---

### Post by TeoBigusGeekus on 2011-01-01
Try to see if the extra partition is seen with
```
sudo fdisk -l
```
If so, force mount it somewhere - it will probably contain the system files of your player and, hopefully, what you're looking for.
```
mkdir /media/mp4sys
```
```
sudo mount /dev/whatever /media/mp4sys
```

---

### Post by ttakun on 2011-01-01
> **TeoBigusGeekus said:**
> Try to see if the extra partition is seen with
```
sudo fdisk -l
```
If so, force mount it somewhere - it will probably contain the system files of your player and, hopefully, what you're looking for.
```
mkdir /media/mp4sys
```
```
sudo mount /dev/whatever /media/mp4sys
```

Thank you for replying TeoBigusGeekus, but no good news ;-(
```
$ **sudo fdisk -l**

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0xe35d128e

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        6596    52982338+   7  HPFS/NTFS
/dev/sda2            6597        7901    10482412+  83  Linux
/dev/sda3            7902        8163     2104515   82  Linux swap / Solaris
/dev/sda4            8164        9729    12578895   83  Linux

[COLOR="Red"]Disco /dev/sdb: 16.5 GB, 16526606336 bytes
64 cabezas, 32 sectores/pista, 15761 cilindros
Unidades = cilindros de 2048 * 512 = 1048576 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x6f20736b

Esto no parece una tabla de particiones
Probablemente ha seleccionado el dispositivo que no era.

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   ?      379950      937327   570754815+  72  Desconocido
La partición 1 no termina en un límite de cilindro.
/dev/sdb2   ?       82368     1027695   968014120   65  Novell Netware 386
La partición 2 no termina en un límite de cilindro.
/dev/sdb3   ?      913029     1858355   968014096   79  Desconocido
La partición 3 no termina en un límite de cilindro.
/dev/sdb4   ?     1409025     1409052       27749+   d  Desconocido
La partición 4 no termina en un límite de cilindro.

Las entradas de la tabla de particiones no están en el orden del disco[/COLOR]

```

Sorry it's in Spanish ... but when analyzing sdb it says as it doesn't look as a partition table. Probably I have not selected the correct device. And in the end it says that the entries in the partition table are not in the same order in the disc ¿?

And if I try to mount it as /dev/sdc (because in the **dmesg** at some point **sdc** appers ...) it says:
```
$ sudo mount /dev/sdc /media/MULTIBOOT/
umount: /dev/sdc: dispositivo desconocido

```
/dev/sdc: Unknown device

---

### Post by TeoBigusGeekus on 2011-01-01
Try mounting the sdb partitions one by one (sdb1,2,etc.) and see if you can get something.

---

### Post by ttakun on 2011-01-01
> **TeoBigusGeekus said:**
> Try mounting the sdb partitions one by one (sdb1,2,etc.) and see if you can get something.

Thank you again, but ... :confused:

I unmounted the device, created a dir (ROCKCHIP16GB) to mount the sdb[COLOR="Red"]x[/COLOR] partitions, but only worked with the sdb (with no number)

It said that the special device /dev/sdb[COLOR="Red"]x[/COLOR] does not exist 
> $ sudo umount /dev/sdb
$ sudo mkdir ROCKCHIP16GB
$ ls
MULTIBOOT  ROCKCHIP16GB
$ sudo mount /dev/sdb1 /media/ROCKCHIP16GB/ -t vfat
mount: el dispositivo especial /dev/sdb1 no existe
$ sudo mount /dev/sdb2 /media/ROCKCHIP16GB/ -t vfat
mount: el dispositivo especial /dev/sdb2 no existe
$ sudo mount /dev/sdb3 /media/ROCKCHIP16GB/ -t vfat
mount: el dispositivo especial /dev/sdb3 no existe
$ sudo mount /dev/sdb4 /media/ROCKCHIP16GB/ -t vfat
mount: el dispositivo especial /dev/sdb4 no existe
$ sudo mount /dev/sdb /media/ROCKCHIP16GB/ -t vfat
$ mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda4 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ttattakun/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ttattakun)
/dev/sdb on /media/ROCKCHIP16GB type vfat (rw)
$ ls /media/ROCKCHIP16GB/
demo.txt                                             test03.rm 
hotel california.lrc                                 War3-Movie-Trailer.avi
hotel california.mp3                                 WMPInfo.xml


---

### Post by TeoBigusGeekus on 2011-01-01
My limited knowledge is exhausted, sorry my friend...
Anyone else?

---

### Post by ttakun on 2011-01-01
Anyway ... Thank you very much Teo ):P

---

### Post by TeoBigusGeekus on 2011-01-01
Happy new year ttakun...

---

