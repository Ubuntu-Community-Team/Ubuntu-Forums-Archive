---
title: "Boot Ubuntu from SD card"
date: 2010-09-04
forum: General Help
---

### Post by pacaj2am on 2010-09-04
Hello,

I am trying to boot ubuntu from SD Card, but it fails.

I made bootable SD card from ubuntu-10.04.1-desktop-amd64.iso using Startup Disc Creator.

From bios i selected to boot from SD card, it loades initramfs, but it hanges on

(initramfs) Unable to find a medium containing a live file system

My sdcard reader is ricoh:

```
 *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 9.1
                bus info: pci@0000:85:09.1
                version: 25
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=0 module=sdhci_pci
           *-system:1
                description: System peripheral
                product: R5C843 MMC Host Controller
                vendor: Ricoh Co Ltd
                physical id: 9.2
                bus info: pci@0000:85:09.2
                version: 14
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ricoh-mmc latency=0 module=ricoh_mmc
```

My knowledge is not so big, in my opinion initramfs either don't know where the image of boot system is, but dmesg doesn't show that module ricoh-mmc is loaded: ```
dmesg|grep ricoh
``` shows nothig.

Or i have to add modules for sd card reader to initramfs but i don't kno how.

in bussybox i tried to modprobe richoh-mmc but now output from this command :-(

Thank you in advance for any help.

Jan

---

### Post by Bishamon101 on 2010-09-28
Hey

i've got exactly the same problem. My very small pc has just a sd card reader in it and i want to boot ubuntu. With an attached usb pendrive everything works flawlessly.

My knowledge of ubuntu/linux is very little but i guess the boot image doesn't contain a proper sd module.

can anyone help?

cheers

---

### Post by sgosnell on 2010-09-28
The driver for the card reader is loaded, or else it wouldn't show up as a boot option in the first place.  I think the problem is most likely a bad install on the SD card, or a bad SD card itself.  Try reinstalling the system on the SD card, and if possible, using a different SD card.  1GB SDHC cards, the largest required for a liveUSB install, are very cheap, and are often prone to failure, especially the very cheap ones.

---

### Post by udippel on 2010-10-18
> **Bishamon101 said:**
> Hey

My knowledge of ubuntu/linux is very little but i guess the boot image doesn't contain a proper sd module.

cheers

Are we the only ones??
I'd like to do the same; you're right, support for the SD-card is missing.
In case you managed to include it, please let me know!

Uwe

---

### Post by C.S.Cameron on 2010-10-18
This must be related to the card reader and/or computer.
I just did a Full install to a SD card on an EEE PC and it works fine.

---

### Post by snowpine on 2010-10-18
It depends entirely on your computer's BIOS. Some computers can boot from SD but some can't, and Ubuntu cannot change this. Consult your computer's documentation to learn which is the case.

If you are not able to boot from the internal SD slot, sometimes you can work around this by purchasing an inexpensive USB card reader (assuming the computer supports USB boot).

---

### Post by Veloteuton63 on 2011-06-14
This is an old thread, but I hope someone still reads it ...

Having the same problems (error mesg as above: "(initramfs) Unable to find a medium containing a live file system"), but:
It is neither an SD card nor a card reader / computer / BIOS problem, as the same procedure that is failing with an UBUNTU 11.04 or a MINT Linux 11 image, works perfectly well with another distro: kanotix-2.6.38.iso. I.e. I install it to the SD CARD using 

either YUMI-0.0.2.1.exe  or unetbootin-windows-494.exe

On the other hand: running these images from CDROM or USB stick works just fine. 

Any ideas?

---

### Post by FabHawk on 2011-06-21
Hi,

I have exactly the same issue. Agree with you, this can not be a BIOS problem.
I contacted an expert of my laptop brand HP, here is the answer I got :
 > *[COLOR=#1F497D][FONT=&quot;]&#8220;[/FONT][/COLOR]*I have seen this error a couple of times, meaning the linux boot kernel is unable to build the live system for booting. Especially from some dodgy USB sticks or with older distributions. 
    In your case I can only guess right now. As this is booting from a SD card, it is possible that the kernel that is booted doesn&#8217;t have the drivers to address the SD card. This means the kernel is loaded and at the point, where it would create the live file system, it can&#8217;t get the image from the SD Card.*[COLOR=#1F497D][FONT=&quot;]"[/FONT][/COLOR]*
  
It doesn't really help, but it's a start...
If anybody could build on that...

Regards
F

---

### Post by gandaran on 2011-06-21
> **FabHawk said:**
> Hi,

I have exactly the same issue. Agree with you, this can not be a BIOS problem.
I contacted an expert of my laptop brand HP, here is the answer I got :
 
  
It doesn't really help, but it's a start...
If anybody could build on that...

Regards
F
I tried booting from the SD card on my Toshiba netbook, the BIOS wont boot it but if I use the SD card in an external usb card reader and choose the usb option it boots just fine, so what is the problem? I think it must be BIOS that is not prepared to boot from internal card readers, maybe I'm wrong, I would like to know.

---

### Post by FabHawk on 2011-06-21
> **gandaran said:**
> I tried booting from the SD card on my Toshiba netbook, the BIOS wont boot it but if I use the SD card in an external usb card reader and choose the usb option it boots just fine, so what is the problem? I think it must be BIOS that is not prepared to boot from internal card readers, maybe I'm wrong, I would like to know.

I don't know about your BIOS, you need to check that with your manufacturer. but on my side SD is bootable.

I think your problem is more related to the support of your internal SD card reader by Ubuntu...

---

### Post by C.S.Cameron on 2011-06-21
My older Asus laptop will not boot SD card from the built in reader, my EEE PC will.

---

### Post by Mr.Dee on 2011-06-21
I'm not sure I understand all the output the OP pasted.  So all I have to say is unetbootin?  Actually,  I've only had success in creating an ubuntu bootable usb/sd with startup disk creator from within a live version of ubuntu.

---

### Post by dforionstar on 2011-06-24
> **gandaran said:**
> I tried booting from the SD card on my Toshiba netbook, the BIOS wont boot it but if I use the SD card in an external usb card reader and choose the usb option it boots just fine, so what is the problem? I think it must be BIOS that is not prepared to boot from internal card readers, maybe I'm wrong, I would like to know.

gandaran: Are you able to tell us *exactly *what external USB card reader you are using? I am looking for a USB card reader for my 8 GB SDHC card as I am are able to boot to USB in the BIOS but not SD.

Thanks in advance!

---

### Post by Darwinsky on 2011-07-01
Same problem here, i have an Eee Pc 901 GO and i need to reinstall the OS since my Network Manager interface is gone (apparently not an unusual problem). In boot order option i have only 3 alternatives; CD, HDD (SSD in my case i guess) and "external device", which would be USB and maybe also SD card. The strange thing is that i have managed to boot and install from my SD card once before already but that was when Windows was installed, but now when having Ubuntu it doesn't seem to work, Windows - Ubuntu 1-0 i guess? ;) (Just joking). But it is kind of strange, don't you think? 

Disclaimer: I'm a total noob, so if got something wrong, go easy...

---

### Post by willykilly on 2011-08-24
Hi,
 I have a rootfs and kernel bzimage. How to install them along with grub to an SD card so that it boots correclty.
Thanks.

---

