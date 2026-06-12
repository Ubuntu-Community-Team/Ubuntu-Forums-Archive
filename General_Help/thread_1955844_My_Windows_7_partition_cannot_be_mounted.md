---
title: "My Windows 7 partition cannot be mounted"
date: 2012-04-10
forum: General Help
---

### Post by kronos34 on 2012-04-10
Hi all, 

I came this morning to finish an urgent job but my Windows 7 partition cannot be mounted (all my files are in there!!) and I cannot boot the Windows 7 SO neither. The partition worked before the weekend, I just copied a lot of files in there, exited and went home!

The computer has a partition with Windows 7 (SO and data), and the usual partitions for booting, Ubuntu 10.01LTS and swap. 

When I do a fdisk -l I get the following:

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x0006660a

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
La partición 1 no termina en un límite de cilindro.
/dev/sda2              13       42200   338868076    7  HPFS/NTFS
/dev/sda3           42201       60801   149412502    5  Extendida
/dev/sda5           42201       60047   143355996   83  Linux
/dev/sda6           60048       60801     6056473+  82  Linux swap / Solaris

Please, do you know how can I boot the W7 system again? :(

Thanks!

---

### Post by zeljkojagust on 2012-04-10
Did you try ```
sudo mount /dev/sda2 /mnt
```?
If that is not successfully you are probably missing ntfsprogs package.
Install it ```
sudo apt-get install ntfsprogs
```, and try the upper command again. Let us know how did it go.

---

### Post by kronos34 on 2012-04-10
The ntfsprogs was already installed in its last version. 

When I do $sudo mount /dev/sda2 /mnt, nothing happens... :(

Any other hint?? Thanks!

---

### Post by zeljkojagust on 2012-04-10
If mount exits on command prompt with no messages, that's good. It means it has successfully mounted your NTFS partition to /mnt folder. Did you check it's content after performing mount?

---

### Post by kronos34 on 2012-04-10
It didn't return any message, but there are no folders in /mnt, neither in /media... 

thanks again for your help! could it be related to the cylinders limit?

---

### Post by Mark Phelps on 2012-04-10
If you're mounting your Win7 OS partition in Ubuntu and writing files their from Ubuntu, you just found out the hard way that is a BAD thing to do -- it risks corrupting the Win7 OS filesystem, which apparently is what happened.

IF you can't boot into a Win7 desktop, then try booting into SAFE mode in Win 7 and running CHKDSK.  Keep pressing the F8 key while booting Win7 and see if it eventually gets you a menu screen where you can choose SAFE mode.

---

### Post by kronos34 on 2012-04-10
I'll check to start the Win7 with the F8 key to get into the safe mode, thanks.

In any case, the situation doesn't look good as I currently use three computers with a similar partition scheme: a Win7 partition containing all the data and the SO, and the Ubuntu installation, that I usually employ for accessing the data files in the Win7 partition. I didn't know it could cause any trouble to the Win7! 

So, how should I access both Win7 and Ubuntu files in the same computer? I frequently need to change from one to another SO depending on the program I use. Should I create a double Win7 partition to separate the data and the SO?

cheers!
Victor

---

### Post by forrestcupp on 2012-04-10
If Windows doesn't get shut down properly, you can't access that partition from Ubuntu. The way you fix it is to boot back into Windows, and make sure it shuts down properly, then boot back into Ubuntu and it will work.

Hopefully, you're able to get it booted into Safe Mode. If you can't do that, I don't know what you would do because you probably couldn't even access it from a LiveCD. Maybe you'd have to boot to a Windows installation CD/DVD and choose to repair the installation.

---

### Post by Mark Phelps on 2012-04-10
[QUOTE=kronos34;11833087]... So, how should I access both Win7 and Ubuntu files in the same computer? I frequently need to change from one to another SO depending on the program I use.../QUOTE]

Good question! And the answer is ... create a shared NTFS DATA partition.  Since Data partitions aren't booted, you don't have to worry nearly so much about filesystem corruption.  And, if you DO have a problem, you simply boot into Win7 and run CHKDSK on the Data partition and it's usually OK again.

---

