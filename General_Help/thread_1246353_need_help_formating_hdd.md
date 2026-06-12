---
title: "need help formating hdd"
date: 2009-08-21
forum: General Help
---

### Post by umdoobby on 2009-08-21
could someone plz tell me how to format my 80 gig external hdd

---

### Post by kanikilu on 2009-08-21
I'd use gparted: ```
gksu gparted
``` Just be sure you are formatting the intended drive!

I'm not sure if it's installed by default, so you may need to find it in synaptic or install it with apt-get.

---

### Post by cwaidelich on 2009-08-21
First do

```
sudo fdisk -l
```

this lists all your partitions.

there you will see a list of all your partitions starting like this:

```

<!-- THIS IS MY INTERNAL HDD-->

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x00070605

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       60436   485452138+  83  Linux
/dev/sda2           60437       60801     2931862+   5  Extendida
/dev/sda5           60437       60801     2931831   82  Linux swap / Solaris

<!-- THIS IS MY EXTERNAL USB DRIVE-->

Disco /dev/sdb: 1035 MB, 1035993088 bytes
22 cabezas, 53 sectores/pista, 1735 cilindros
Unidades = cilindros de 1166 * 512 = 596992 bytes
Identificador de disco: 0x04030201

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1        1736     1011592    b  W95 FAT32

```


Then do ```
sudo gparted /dev/sdb (in my case, I want to format the USB stick)

This is secure because you wont touch the internal HDD!!!

```

Then it is actually pretty easy to format it.

Cheers.

---

### Post by ajgreeny on 2009-08-21
Should really be ```
gksudo gparted
``` as it's a gui application.

You can either do it by installing gparted to your system, or you can use the Live CD which has it installed by default.  Open gparted (System > Administration >Partition Editor) and make sure you find the right drive in the drop-down box top right.  You will probably need to right click the partitions on it and choose unmount before you can do anything to it, but then it's all quite self explanatory.

Just make sure you do it to the right drive, or you're in trouble.  It should be obvious from the size of the drive, and from the nimber of hard drives in the machine.

---

### Post by umdoobby on 2009-08-22
i enter the command but nothing happens

---

### Post by gastly on 2009-08-22
You will first need to install gparted.
```
sudo apt-get install gparted
```

Be sure to unmount the drive that you wish to modify, **before** doing any changes.

The safest way to modify the partitions is to boot from a livecd and then change the partitions (as ajgreeny suggested).

---

### Post by umdoobby on 2009-08-22
i have a Neuros OSD media recorder that im going to use this drive with what system should i use to format the drive

---

### Post by umdoobby on 2009-08-22
never mind i got it thanks for the help

---

