---
title: "Ubuntu install help using external dvd drive"
date: 2010-02-06
forum: General Help
---

### Post by iamlovelyboy on 2010-02-06
All,
i ve got a complicated isssue. I have a Compaq presario v2000 where my cd drive doesnt work. The only boot options i have are 1. boot from cd 2. network 3. floppy and 4. hard drive. Ive got an external cd drive and i have a cd ready to install ubuntu. How do i install it? ANy suggestions appreciated. Thank you very much in advance

---

### Post by efflandt on 2010-02-06
I inherited one of these when I bought someone a new laptop.  It is a low end laptop and apparently has minimal BIOS which has no way to boot from USB (other that booting from CD/DVD that could then boot USB).

This V2000 has a combo CD-writer/DVD.  Are you sure that it cannot read CD or DVD (different sensors) or is the motor shot?

Best bet may be to install Ubuntu 9.10 using another computer, either as its drive or external USB drive enclosure.  But if not the primary drive of the computer being installed from, you have to make certain that you pay attention to the **Advanced** button in the summary screen, just before the actual installation proceeds, to put grub on the mbr of that drive, instead of default to mbr of primary drive.

That should work because Ubuntu uses UUID to identify drives (I have a USB drive that boots fine whether it ends up as sdb or sdf).

Initially the keyboard may seem unresponsive (might have to press some keys twice to log in) with erratic mouse movements.  Not sure if that is the result of video or old Winmodem, but it seems responsive now that video package and modem driver below have been installed:

xorg-driver-fglrx (for ATI video)
Broadcom B43 wireless driver (or b43-fwcutter package)
Software Modem driver (or sl-modem-daemon package)

Be cautious about using suspend or hibernate, since it may wake up to a dead screen and/or no key/mouse response.  So it may be best to set Power Management settings to shutdown if lid is closed or power button is pressed.

It initially has some issues, but works well enough once you get everything set up (I am posting this from it).

Output of lspci:```

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
```

---

### Post by switch10 on 2010-02-06
you will be able to install Ubuntu if your BIOS supports USB devices.  Look for a setting like "legacy USB" and enable it.  then restart, and see if your Bios can use your USB drive to boot from.

Good luck

Dave

---

### Post by warp99 on 2010-02-06
You can make a boot floppy, then chain-load to a USB pendrive:

[http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/](http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/)

Edit: You can also chain-load to a CD-Rom but you would need to edit the grub floppy menu.lst, which is a much more involved process.

---

