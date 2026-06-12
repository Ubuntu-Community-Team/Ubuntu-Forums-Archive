---
title: "4Gb SD does not work in 10.04 64bit"
date: 2010-05-28
forum: General Help
---

### Post by n-alexander on 2010-05-28
1. a 2Gb SD works in this PC with 10.04 Kubuntu
2. a 4Gb SD does NOT - nothing happens
   nothing in dmesg when I insert the card, 
   manual mount fails - can not see VFAT on it
3. this same 4Gb SD works with 9.10 netbook remix on a Lenovo laptop - auto mounts fine
4. I do believe this card worked in this PC when it had 9.10 on it. Or XP.

So I think the card is fine, and the reader in the PC is fine, too. 

Where do I look?

Thanks,
Alex

---

### Post by chessnerd on 2010-05-28
I have a 4GB SDHC card that I always leave in on my laptop. It works fine with 10.04 64-bit. However, it didn't work the first week or so. Make sure you have your system fully updated.

Also, what filesystem is the card using? Is it FAT32?

---

### Post by tgalati4 on 2010-05-28
Plug the card into a camera and connect the camera with USB to the computer and see if it mounts.  I have a wonky card reader that has problems with Intrepid 64-bit.  Works fine if I stick the SD card in an old HP printer with a card reader.  Go figure.

Also realize that when crossing the 2 GB border that the cards go from SD to SDHC with slightly different specifications.  It's possible that your reader doesn't follow the SDHC specs or there is a driver problem or a USB detection problem.

My guess is the latter.  I would file a bug against udev (the hardware detector that replaced HAL).

But do your updates first as chessnerd suggested.

---

### Post by efflandt on 2010-05-28
Some card readers in laptops, etc. do not end up as sd devices, but instead as a different type of block device.  And not not all 4 GB SD are SDHC, although, they may be faster than older 2 GB or smaller SD.

I have a 4 GB SD I got with a camera that is not HC, but it is 133x (or x133?).  It does not work in the card slot of my 2006 Toshiba laptop, but works in the same laptop in a relatively old Lexar USB SD reader.  The Toshiba will not boot any SD in its card slot, but will boot SD (or even microSD) in a USB card reader.  So try a USB card reader and see if that works.

---

### Post by jondodson on 2010-05-28
SD readers/writers cannot read/write SDHC Cards.  Different hardware specs.  Vice versa works though.

---

### Post by kuckunniwi on 2011-01-17
> **jondodson said:**
> SD readers/writers cannot read/write SDHC Cards.  Different hardware specs.  Vice versa works though.

I'm having the same problem with an 8Gb SDHC card on a brand new HP mini 110 3050ss running Kubuntu Lucid 64-bit.Under the "PC card slots" of the product specifications, it states *2-in-1 integrated Digital Media Reader for Secure Digital cards and MultiMedia cards.*, but it seems odd that the card would work fine on a 2 year-old Clevo laptop (running Ubuntu Lucid) and not a brand new netbook. I think it may be more of a Kubuntu 10.04 issue...



$ lspci -tv
```
-[0000:00]-+-00.0  Intel Corporation N10 Family DMI Bridge
           +-02.0  Intel Corporation N10 Family Integrated Graphics Controller
           +-02.1  Intel Corporation N10 Family Integrated Graphics Controller
           +-1b.0  Intel Corporation N10/ICH 7 Family High Definition Audio Controller
           +-1c.0-[0000:01]--+-00.0  Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller
           |                 \-00.1  Realtek Semiconductor Co., Ltd. Device 5288
           +-1c.1-[0000:02]----00.0  RaLink RT3090 Wireless 802.11n 1T/1R PCIe
           +-1d.0  Intel Corporation N10/ICH7 Family USB UHCI Controller #1
           +-1d.1  Intel Corporation N10/ICH 7 Family USB UHCI Controller #2
           +-1d.2  Intel Corporation N10/ICH 7 Family USB UHCI Controller #3
           +-1d.3  Intel Corporation N10/ICH 7 Family USB UHCI Controller #4
           +-1d.7  Intel Corporation N10/ICH 7 Family USB2 EHCI Controller
           +-1e.0-[0000:03]--
           +-1f.0  Intel Corporation NM10 Family LPC Controller
           +-1f.2  Intel Corporation N10/ICH7 Family SATA AHCI Controller
           \-1f.3  Intel Corporation N10/ICH 7 Family SMBus Controller

```

---

### Post by kuckunniwi on 2011-01-29
Alex, what computer & SD card are you using?

I'm running Kubuntu 10.04 of an HP mini 110 3050ss, and was having the same problem, but was able to find the drivers for my realtek card-reader, and once installed, they worked flawlessly.

---

