---
title: "Partition Assistance"
date: 2009-07-17
forum: General Help
---

### Post by devosion on 2009-07-17
I've had my desktop computer on an on-again off-again basis for dual-booting with Vista and Ubuntu. Today I am going to reinstall Vista, after several months of stress free computing, in order to try to get my gaming habit going again, but I have a few questions as I do this.

My first has to do with my two drives. I have a 150gb sata hd I have ubuntu installed to, and a 70gb IDE hd that I have formatted to ntfs for Vista. When I checked my fstab I noticed that my IDE drive is listed before my sata drive. I do not remember configuring it this way, and this may be a hurdle for me while I fiddle with grub later. Why did Ubuntu place the hard drives in this order, and is there an easy way to clear the MBR of the IDE drive since the last time I used this setup grub wouldnt load for me?

And since the drives are already listed in this order, if I could change the device order would that allow my ubuntu install, and the /boot partition, to take precedence over the MBR install of Vista on the second drive?

Lastly I could use any advice for tackling this dual-boot situation since each time I approach dual-booting I usually have the issue where Vista doesn't allow grub to load at all. 

The configuration looks like this if it helps:

/dev/sda | 70gb | Vista | Vista installed bootloader
/dev/sdb | 150gb | Ubuntu | /root /home /boot <--- grub

Thanks!

---

### Post by devosion on 2009-07-17
OK, guys I could really use some help right about now because my installation for Vista went through and it loads up as it should. The problem is that it loads into Vista without loading into grub as it had before.

I am currently trying to install grub on the ntfs partition but it returns.

Error 17: Cannot mount selected partition

After I run setup(hd0) from the grub command line. Is this because its NTFS? If that's the case then is there a way I can install grub on /dev/sda so I can overwrite the Vista bootloader?

I am currently staring at the Vista boot loader on my Ubuntu Live CD and I dont know if deleting it will help, or just cause Vista to perform a repair. I'd really prefer not to use the likes of Neogrub and Windows bootloaders to get to Ubuntu since i've become partial to grub.

---

### Post by merlinus on 2009-07-17
Post results of

```
sudo fdisk -l
```

Also, what is the booting order of your hdds in bios?

---

### Post by devosion on 2009-07-17
> Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9726    78124063+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f4f8f4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         851     6835626   83  Linux
/dev/sdb2             852       19335   148472730   83  Linux
/dev/sdb3           19336       19457      979965   82  Linux swap / Solaris


And the hard drive order in my bios is always the IDE before the SATA drive. No amount of trying to change this configuration works and it irritates me to no end.

---

### Post by merlinus on 2009-07-17
You might try this:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd1,0)
root (hd1,0) #use the numbers from the previous command
setup (hd0)
quit
```

and restart.

---

### Post by devosion on 2009-07-17
o.O Ok you must have the magic touch, or something along those lines, because this is the first time in a year that i've inputted those lines, and i've tried those exact commands countless times to error 17 before, but now it went through flawlessly. All I need to do now is setup a grub entry for Vista. Thanks very much.

Quick question though, is editing the menu.lst on my boot partition in ubuntu the correct file to edit to add an entry for Vista?

---

### Post by merlinus on 2009-07-17
/boot/grub/menu.lst

add the windows stanzas at the very end of the file.

Glad I could assist a fellow New Mexican!

---

