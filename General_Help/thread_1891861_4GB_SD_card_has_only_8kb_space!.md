---
title: "4GB SD card has only 8kb space!"
date: 2011-12-06
forum: General Help
---

### Post by arzali on 2011-12-06
Hi all.
I have a 4GB sdcard but it doesnt show in the file manager as a drive.
opening gparted it shows it as a 8.0 KiB drive.
trying ro format it, i get:
```

$ sudo mkfs.vfat /dev/sdf1
mkfs.vfat 3.0.9 (31 Jan 2010)
mkfs.vfat: Attempting to create a too large file system

```

is there a way to get the card to work?

---

### Post by fdrake on 2011-12-06
what is the output of:
```

sudo fdisk -l

```

---

### Post by arzali on 2011-12-06
output is in german
```

Platte /dev/sdf: 0 MByte, 8192 Byte
1 Köpfe, 1 Sektoren/Spur, 16 Zylinder, zusammen 16 Sektoren
Einheiten = Zylinder von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000385e8

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdf1   *           2          16           7+   c  W95 FAT32 (LBA)


```

---

### Post by LinuxFan999 on 2011-12-06
It looks like your SD card might be failing.

How old is it?

---

### Post by arzali on 2011-12-06
its new. unpacked it yesterday X)

---

### Post by phidia on 2011-12-06
Either you bought a fraudulent sd card a lot of those were selling on ebay a while ago or you need to contact the seller about a replacement.

---

### Post by bluexrider on 2011-12-06
> **arzali said:**
> its new. unpacked it yesterday X)

send it back, there is just to much of a chance it bad

---

### Post by fdrake on 2011-12-06
@arzali

did you try to read write the sd card with another sys: OsX or win? do the show the same error?

---

### Post by pqwoerituytrueiwoq on 2011-12-06
check it with the disk utility see how big the partition is
i fixed a person's new flash drive that "did not work" it was not partitioned

---

### Post by arzali on 2011-12-06
@fdrake tried with win7 and several formating tools (hp, panasonic etc.) all say that there is an error and cant format it.

@pqwoerituytrueiwoq checked with disk utility and its the same as with gparted, it shows only 8kib space :/

Aren't there some hardcore linux formating or swiping tools where i could force formating?
I don't care if it has a gui or not just something i could try.

---

### Post by bluexrider on 2011-12-06
> **arzali said:**
> @fdrake tried with win7 and several formating tools (hp, panasonic etc.) all say that there is an error and cant format it.

@pqwoerituytrueiwoq checked with disk utility and its the same as with gparted, it shows only 8kib space :/

Aren't there some hardcore linux formating or swiping tools where i could force formating?
I don't care if it has a gui or not just something i could try.

If you had to force it to format I would question the stability of and the quality of the drive.

DUMP IT!

---

### Post by theozzlives on 2011-12-06
> **bluexrider said:**
> If you had to force it to format I would question the stability of and the quality of the drive.

DUMP IT!

I agree, get your money or a replacement from the seller!

---

### Post by arzali on 2011-12-07
Update: i somehow managed to get it work. 
I just formated it several times with usb-creator and now it shows 4gb :)

Thanks for all suggestions

---

### Post by bluexrider on 2011-12-07
> **arzali said:**
> Update: i somehow managed to get it work. 
I just formated it several times with usb-creator and now it shows 4gb :)

Thanks for all suggestions

wonder how long that's gonna last. too bad you can't predict the fail date. I wouldn't put anything valuable on it. 

I just had a PNY 32GB super SD media card fail with over 150 pictures of my last photo-shoot. can ya say ooooohhhhh crap

Gook Luck

---

### Post by arzali on 2011-12-08
> **bluexrider said:**
> wonder how long that's gonna last. too bad you can't predict the fail date. I wouldn't put anything valuable on it. 

I just had a PNY 32GB super SD media card fail with over 150 pictures of my last photo-shoot. can ya say ooooohhhhh crap

Gook Luck
Not so long XD
I tried to copy a linux image on it but after a reboot i have 8kib space again :P

---

