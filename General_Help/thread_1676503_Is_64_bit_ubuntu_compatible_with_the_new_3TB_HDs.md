---
title: "Is 64 bit ubuntu compatible with the new 3TB HDs?"
date: 2011-01-27
forum: General Help
---

### Post by cptrohn on 2011-01-27
Pretty simple question I guess?  I know that 32 bit windows won't recognize it as 3TBs... I have read that 64 bit windows will with some extra software... my question is will ubuntu recognize the drive as 3 TBs?  I just ask because I am currently building a Myth box and would LOVE to have that capacity of storage for all my media.

---

### Post by justleen on 2011-01-27
Not as a bootdisk, but only as a secondary disk. AFAIK.

---

### Post by Kirboosy on 2011-01-27
It might work as a boot disk. You have a better chance of it working with Ubuntu 64 bit...If it doesn't work right then you can always have the 3 TB as a Data drive and a small hard drive to boot Ubuntu/MythTV

---

### Post by coffeecat on 2011-01-27
I don't know about any difference between 32 and 64-bit Windows, but I believe the problem with Windows is the 2TB partition size limit with drives partitioned with the mbr partition table - the usual default. You need to use a GUID partition table (GPT) to get around that limit. Windows 7 (don't know about XP) is happy with GUID partitition tables (unless trying to boot from a BIOS machine) so I'm not sure what the software is that you mention. Whatever - with Ubuntu you should be fine (with a GUID partition table) and with a 1 exabyte limit on volumes in ext4 you have a long way to go before you exceed that!

---

### Post by justleen on 2011-01-27
Only OS'es with EFI/GPT can use it as a boot disk.
Ubuntu supports GPT, but im sure if it works with a default installation.

The whole i386 / x64 has nothing to do with this.

Check these links
[http://www.delltechcenter.com/page/3TB+drives%3A+OS+Behavior+Matrix](http://www.delltechcenter.com/page/3TB+drives%3A+OS+Behavior+Matrix)
(bottom of the table)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by cascade9 on 2011-01-27
Which HDD? The WD 'green power' drivers come with a PCIe HBA (host bus adapter) because on release, most BIOSes wont recognise the 3TB drive. 

You really need the BIOS to recognise the drive, or a HBA, or else you wont be able to use the drive. (though to be more exact, you need uEFI )   

I'd doubt that windows 64 (or 32 for that matter) will recognise a drive that the BIOS cant see, or fix the drive from whatever size BIOS decides it is (746GB ssems to be common) no matter what software you throw at it. 

I dont know if ubuntu would recognise the drive as 3TB. That would depend on the version you are using ;) 

I would avoid the 3TB drives for now, utill the compatibility issues are ironed out. If you really had to have one, use it as a secondary drive, not a boot drive.

---

### Post by srs5694 on 2011-01-27
> **justleen said:**
> Only OS'es with EFI/GPT can use it as a boot disk.

That's incorrect. You can boot Linux from a GPT disk on a BIOS-based computer. I'm typing this on such a computer (although it uses Gentoo, not Ubuntu), and I've got several others (including an Ubuntu box) that work the same way.

For the most part, the requirement to have EFI to boot from GPT is a Windows requirement, not a BIOS requirement. There are a few exceptions in the form of buggy BIOSes, but AFAIK, most or all such bugs can be worked around in one way or another. See [this Web page of mine](http://www.rodsbooks.com/gdisk/bios.html) for details.

> Ubuntu supports GPT, but im sure if it works with a default installation.

It does.

> The whole i386 / x64 has nothing to do with this.

This is true in terms of Linux on a GPT disk in general, and even Linux's support of > 2 TiB drives in general (I've tested in virtual machines). There is a link when you toss EFI into the mix, though -- it's harder to boot a 32-bit OS on a machine with a 64-bit EFI than it is to boot a 64-bit OS on that same machine. I'm a little foggy on the details of what doesn't work, but it has something to do with Linux getting access to data and support from the EFI.

> Check these links
[http://www.delltechcenter.com/page/3...ehavior+Matrix]("http://www.delltechcenter.com/page/3TB+drives%3A+OS+Behavior+Matrix")
(bottom of the table)

Note the table assumes booting using EFI. As I've said, EFI isn't necessary to boot Linux from a GPT disk. That table is more of an issue if you were interested in buying an EFI-only motherboard.

[quote=cascade9]Which HDD? The WD 'green power' drivers come with a PCIe HBA (host bus  adapter) because on release, most BIOSes wont recognise the 3TB drive. 

You really need the BIOS to recognise the drive, or a HBA, or else you  wont be able to use the drive. (though to be more exact, you need uEFI )[/quote]

Aside from the incorrect statement that "you need uEFI," this is a good point, and it's the only question mark in my own mind. If the BIOS doesn't recognize the drive, you won't be able to boot from it no matter what (but see below). I know that one of the reasons WD fakes a 512-byte sector size on its newer drives that in fact use 4096-byte sectors is that some BIOSes assume a 512-byte sector size. If there's a 3 TB drive that exposes its true 4096-byte sector size, then you'd still be able to use MBR with it, but if you've got a BIOS (or boot loader or anything else) that makes 512-byte sector-size assumptions, you're in trouble. Likewise if the BIOS assumes drives won't exceed a certain size -- although in the past, problems like that were usually easily overcome by creating a small /boot partition within the part of the drive that the BIOS *could* see.

This last observation leads to an easy workaround if the drive is in fact unbootable because of BIOS issues: You could put your /boot partition and GRUB boot sector on a USB flash drive and boot that way. Once GRUB (loaded from the flash drive) loads the kernel and initial RAM disk (from the flash drive), Linux is in control, and Linux's limitations, not the BIOS's, become important. This solution assumes that you've got a BIOS that can boot from a USB flash drive, of course. Likewise, you could use some old klunker hard disk in a similar way, although that might not be a good solution if you want to build a computer in a very small case.

---

### Post by cptrohn on 2011-01-27
> **cascade9 said:**
> Which HDD? The WD 'green power' drivers come with a PCIe HBA (host bus adapter) because on release, most BIOSes wont recognise the 3TB drive. 

You really need the BIOS to recognise the drive, or a HBA, or else you wont be able to use the drive. (though to be more exact, you need uEFI )   

I'd doubt that windows 64 (or 32 for that matter) will recognise a drive that the BIOS cant see, or fix the drive from whatever size BIOS decides it is (746GB ssems to be common) no matter what software you throw at it. 

I dont know if ubuntu would recognise the drive as 3TB. That would depend on the version you are using.

I would avoid the 3TB drives for now, utill the compatibility issues are ironed out. If you really had to have one, use it as a secondary drive, not a boot drive.

I was actually thinking of this drive.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822145472](http://www.newegg.com/Product/Product.aspx?Item=N82E16822145472)

I am still in the process of selecting which hardware I want to use for the build, and thought I would check to see first.  I might get an SSD for the boot drive and then perhaps get the 3TB as a mass storage drive as was suggested then.

Thanks to everyone for all the great answers!

---

### Post by cascade9 on 2011-01-27
I was wondering how long it would take untill srs5694 showed up. :lolfalg: 

> **srs5694 said:**
> Aside from the incorrect statement that "you need uEFI," this is a good point, and it's the only question mark in my own mind. If the BIOS doesn't recognize the drive, you won't be able to boot from it no matter what (but see below).

Damn, either I misread or teh article I was reading was wrong. Sorry about that, thanks for clearing things up srs5694 ;) 

Nice solution. Not what I would do, which is avoid 3TB until the smoke has cleared, but still nice.  

> **cptrohn said:**
> I was actually thinking of this drive.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822145472](http://www.newegg.com/Product/Product.aspx?Item=N82E16822145472)

I am still in the process of selecting which hardware I want to use for the build, and thought I would check to see first.  I might get an SSD for the boot drive and then perhaps get the 3TB as a mass storage drive as was suggested then.

Thanks to everyone for all the great answers!

A SSD for myth? OK, if it floats your boat. I wouldnt bother, no real need for the speed of a SSD in myth box IMO. 

Without a HBA, you would need the BIOS to support 3TB drives. Some BIOS do, but most dont. You would need to check if the motherboard you are planning on running has 3TB support. 

$25 extra would get you 3 x 1.5TB drives. Run in RAID5 you would get the same storage space, and some data protection. Or (insert half a dozen other options) ;)

---

### Post by srs5694 on 2011-01-27
> **cascade9 said:**
> Damn, either I misread or teh article I was reading was wrong. Sorry about that, thanks for clearing things up srs5694 ;) 

There's a lot of misinformation out there, particularly in the Windows world, about booting from GPT. People tend to assume that Windows' limitations are those of the BIOS. FWIW, the BIOS really has no need to understand any partition table; it doesn't store data on disk, so it just needs to initialize the hardware, read the boot sector, and execute the code it contains. That said, as illustrated by the few buggy BIOSes that *do* have problems with GPT, it's clear that at least some BIOSes make the attempt to parse the partition table. It's unclear to me why they bother, since it's not the BIOS's place to do so.

EFI is different, BTW; by design, it's supposed to be able to read drivers from an EFI System Partition (ESP), so EFI has both the capability and the need to read partition tables. The EFI spec says EFI should be able to boot from both GPT and MBR disks, but once again, OSes can impose their own limitations. On EFI-based systems, Windows requires GPT; it won't boot from MBR disks. (Or so I've heard.) Likewise for Mac OS X. I expect you could boot Linux from an MBR disk on an EFI-based system, but I've not tested this.

> Nice solution. Not what I would do, which is avoid 3TB until the smoke has cleared, but still nice.

Putting /boot on a USB flash drive is sort of a last-resort option -- if you take a gamble on the drive, find that the BIOS chokes on it, and want to rescue the $200 spent, it'll do the job with a minimum of inelegance. I tend to agree that the 3 TB drives aren't worth getting just yet; I generally stay away from the top-of-the-line stuff because it's usually not very cost-effective....

> $25 extra would get you 3 x 1.5TB drives. Run in RAID5 you would get the same storage space, and some data protection. Or (insert half a dozen other options) ;)

This sounds like a better option to me, at least if the computer has a big enough case and you don't mind the extra noise, heat, and energy consumption.

---

### Post by cascade9 on 2011-01-30
> **srs5694 said:**
> There's a lot of misinformation out there, particularly in the Windows world, about booting from GPT. 

Thanks srs5694, I though that might be the case. You know far more about HDDs than I do, so its nice to hear an expert say that there is a lot of misinformation out there....and to know that its not just me making a stupid mistake. ;)

---

### Post by Gralgrathor on 2011-04-20
Rather than partitioning my new WD "green" 3TB drive, I formated the base device ext4. The filesystem wrote to disk okay, so I guess it'll hold data. I'm not using it as boot device, of course; I prefer my OS devices to be slim and fast, and physically separate from data storage.

---

