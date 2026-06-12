---
title: "Grub error 15 after Ubuntu 9.10 installation"
date: 2009-11-01
forum: General Help
---

### Post by willebil on 2009-11-01
I have two discs in my system of each 500Gb, first disc (/dev/sda) holds pre-installed Windows, second one is my Ubuntu installation. After I did a new installation I rebooted my system, and then Grub halts with the following error:

Grub Error 15 : File not found

I have been checking various posts and I found out that Grub cannot find the menu.lst file. The strange things is that I can boot the system by using the BIOS boot disc order and select the second disc as boot disc, then the old boot menu is rendered.

I validated the /boot/grub directory on the new 9.10 install, there was no menu.lst. I recreated it using 'update-grub' only adding the Linux volume, but when I rebooted the same problem persisted.

This is the only way I can start my system, anyone have an idea on how I can fix this problem?

Some additional information:

```
sudo fdisk -l

Schijf /dev/sda: 500.1 GB, 500107862016 bytes
255 koppen, 63 sectoren/spoor, 60801 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x36a6a0b1

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1               1        1274    10233373+  12  Compaq diagnostiek
/dev/sda2   *        1275       31055   239210496    6  FAT16
/dev/sda3           31055       60802   238941184    7  HPFS/NTFS

Schijf /dev/sdb: 500.1 GB, 500107862016 bytes
255 koppen, 63 sectoren/spoor, 60801 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0xd04aa626

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1   *           1       59321   476495901   83  Linux
/dev/sdb2           59322       60801    11888100    5  Uitgebreid
/dev/sdb5           59322       60801    11888068+  82  Linux wisselgeheugen

Schijf /dev/sdg: 400.1 GB, 400088457216 bytes
255 koppen, 63 sectoren/spoor, 48641 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x1c8b1e22

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdg1               1       48641   390708801    c  W95 FAT32 (LBA)

```

```
sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=a1853cbd-0d69-4bfc-b622-2a7872b0039f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=8ed3a95a-00c0-47a7-8b40-aca73d48ac63 none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by P4man on 2009-11-01
9.10 uses grub2 which doesnt use menu.lst anymore. To update grub2 run
sudo update-grub2

---

### Post by willebil on 2009-11-01
> **P4man said:**
> 9.10 uses grub2 which doesnt use menu.lst anymore. To update grub2 run
sudo update-grub2

That is certainly a step forward since Grub2 now finds all partitions and host operting systems properly, see information below.

```
sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done

```

But when I reboot, I still get the Grub error 15 and the system halts. The only way I can restart the system is manually change the disc to boot from in the BIOS or use the live CD for booting.

Somehow I am under the impression Grub needs to be updated on the first disc, but I am not sure...

---

### Post by P4man on 2009-11-01
Looks like you have grub2 installed on the second disc, rather than the first from which your bios boots. id simply change the boot order in the bios.  Or reinstall grub2 on the correct disk from the livecd.  You should find a how to if you search here or on google

---

### Post by willebil on 2009-11-01
> **P4man said:**
> Looks like you have grub2 installed on the second disc, rather than the first from which your bios boots. id simply change the boot order in the bios.  Or reinstall grub2 on the correct disk from the livecd.  You should find a how to if you search here or on google

Murphy must be here, in the BIOS I cannot change the boot discs (although they are there), I can only select the boot disc by the boot-dics-order option on startup.

You suggestion makes sense, looking for some links that describe what I need to do (will post the solution here if I am sucessfull).

---

### Post by willebil on 2009-11-01
I found the following post on the forums that actually solved the problem:

[http://ubuntuforums.org/showthread.php?t=1037538](http://ubuntuforums.org/showthread.php?t=1037538)

```
sudo update-grub2

sudo upgrade-from-grub-legacy

sudo update-grub
```
Select the disc to install grub2 on, /dev/sda in my case, reboot and it worked.

Thanks for the help!

---

### Post by sammynl on 2009-11-01
I had **exactly** the same problem, even the supergrub2 disc couldn't fix it. 
 
I could only get it working by disconnecting all hard drives except the OS disc, do a new clean install and then it all went fine. Not a real solution :( but it is a workaround for me (absolute beginner).

---

