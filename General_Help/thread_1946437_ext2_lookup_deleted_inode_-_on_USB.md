---
title: "ext2_lookup: deleted inode - on USB"
date: 2012-03-24
forum: General Help
---

### Post by originalred20 on 2012-03-24
Hi all!

```
dmesg | grep error
[   31.604807] EXT2-fs (loop1): error: ext2_lookup: deleted inode referenced: 160475
[   31.608542] EXT2-fs (loop1): error: ext2_lookup: deleted inode referenced: 160475
```I used USB installer 1.8.8 to install Ubuntu 11.10. Then I tried Linux Mint 12 and right after reboot, I was getting tons of those errors. I even tried to go back to Ubuntu 10.04 and I used Start Up disk creator and it failed during the installation, giving cd's I/O errors... 
Anyway, what are those errors I put above?
I tried web search, but I didn't get any answer. 

I did what I could. I'm using it on old laptop, that has no HDD. I ran memtest86(version1.4) and it passed. 
Ubuntu and Windows7 says, that formated USB drive (Flash Voyager) are fine...

What can be the cause? What are those erros?

Cheers to all!

---

### Post by imachavel on 2012-03-24
I've only heard of unetbootin to create a bootable OS. I made my linux mint OS bootable actually with a program on windows that didn't use unetbootin. Have not yet been able to get the usb to boot, but everything is good the directories are all there, grub and boot sector are there. I have other files on the pen drive as well that can be dragged and dropped just fine. I can't explain why mine won't boot, but I'm only assuming that old motherboards(or oldish) for some reason really hate booting to bios.

I can't answer your question, but to clarify for others reading this thread, please post the make and model of your computer or laptop that you are trying to boot the pen drive to. Good luck, maybe someone else will direct you to list all the files in the directories, maybe some are more prone to failure and can be recognised as a reason to reinstall the OS with the same program or different program again. Certain things like boot sector and grub are more important to how the OS boots and loads then necessarily the files for what the user will use for programs, apps, etc. once the OS loads. If you do get the OS to load, things like drivers etc. will be very important to what you want to use and the performance of the OS to use programs, applications, sound, video acceleration, internet browser, codecs and plug ins will need to be installed. Sure you know all this. But I don't know what the code needs to look like written in c in the directories for boot sector and grub. Maybe if you create a grub script using boot repair, you can upload the script as an attachment in this thread? Well, I doubt that will allow us to address the issue, unless you are having other hard drive boot/grub issues with the hdd OS loading other then the pen drive when starting your computer. Make sense?

btw, good thing memtest passed. If you had a bsod, memtest SHOULD verify that your processor, ram, power supply, and mobo are all functioning correctly, and that only the hdd could be at fault. But of course the hdd isn't at fault if you can boot into the partition in recovery(terminal shell) mode. In this case, it's the interface not working

---

### Post by originalred20 on 2012-03-25
Thank you imachavel for taking your time.  You're right, I should have listed my specs (!I'm running it on a different distro): ```
lspci -k 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)     Kernel driver in use: agpgart-intel     Kernel modules: intel-agp 00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)     Kernel driver in use: i915     Kernel modules: intelfb, i915 00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) 00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)     Kernel driver in use: uhci_hcd 00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)     Kernel driver in use: uhci_hcd 00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)     Kernel driver in use: uhci_hcd 00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)     Kernel driver in use: uhci_hcd 00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)     Kernel driver in use: ehci_hcd 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) 00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)     Kernel driver in use: Intel ICH     Kernel modules: snd-intel8x0 00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)     Kernel modules: snd-intel8x0m 00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)     Kernel modules: iTCO_wdt, intel-rng 00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)     Kernel driver in use: ata_piix     Kernel modules: ahci 03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)     Kernel driver in use: b44     Kernel modules: b44 03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)     Kernel driver in use: yenta_cardbus     Kernel modules: yenta_socket 03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)     Kernel modules: firewire-ohci 03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)     Kernel driver in use: sdhci-pci     Kernel modules: sdhci-pci 03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)     Kernel driver in use: ipw2200     Kernel modules: ipw2200 
```  It's really hard to determine, what is wrong with this. Right after I posted this, I booted that pendrive with Mint (had the same experience with ubuntu ofcourse) on it. It worked fine. I did some operations, shutdown, turned it on again and dmesg showed no errors at all!  But today in the morning it was almost the same as yesterday. Almost, because it just stopped booting after like 30 seconds. No errors, no nothing, it just stopped.   If it was this Universal installer ([http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)) fault, why would the problems start after second or third boot of a freshly installed system?   PenDrive is my best guess, but I'd like to know for sure.

---

### Post by saponempotenti on 2012-05-28
bump

---

### Post by saponempotenti on 2012-05-28
Not sure why this happens but a simple rienstall of the iso on the live USB will do the trick in fixing. :)

---

### Post by originalred20 on 2012-05-29
> **saponempotenti said:**
> Not sure why this happens but a simple rienstall of the iso on the live USB will do the trick in fixing. :)


True story, but the problem is, that it will occur after like 3rd reboot.... 

I think I forgot to mention, that it's a 3.0 USB pendrive. Anyway, I tried make installation on 2.0 and 3.0 ports and I'm still having the same issue. Recently I used a program called scrub, that erases completely all data by overwriting them. I have rebooted it a couple of times and I thought it's solved the problem, but now. Life of my system without errors increased, but than it died again with those same errors.

---

