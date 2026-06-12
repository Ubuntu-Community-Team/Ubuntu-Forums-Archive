---
title: "booting and running laptop from usb drive"
date: 2012-01-02
forum: General Help
---

### Post by user987 on 2012-01-02
i have ubuntu 11.04 installed on a 16g flash drive and have been able to boot up my dell year 2009 netbook and run the netbook from the flash drive ubuntu os.

i tried the same flash drive on my year 2007 sony notebook and it does not work.

i had gone in to the bios to  enable boot from external/usb device and the boot order of usb first and hard drive as second order.

but when i start the sony my vista os from the harddrive boots and ubuntu don't work.

Why is that? Shoundn't my flash drive work on sony?

Please help.

---

### Post by chipbuster on 2012-01-02
Laptop BIOS systems behave rather strangely sometimes.

Whenever I boot from USB on my laptop, it actually reads the USB as a hard drive. What I have to do is tell it to boot from hard drive, and then (on a completely separate menu), tell it to specify the USB drive as the first boot drive and the internal Hard Drive as the second.

Plug in the USB and poke around a bit in the BIOS. See if there's anything like that. Try disabling your main hard drive (or not including it in the boot order) and see if you can boot anything at all. There might also be a screen that requires you to quickly mash a button to boot from removable devices.

If nothing works, there's a possibility that the BIOS doesn't support boot from USB.

---

### Post by efflandt on 2012-01-02
Sometimes even if you set BIOS to boot USB before internal HD, for safety reasons (virus/worm avoidance) it may still boot the hard drive unless you press a specific key (maybe F12 or Esc) during BIOS splash screen to select boot order.  I have noticed that with Dell laptops.

It is even a little more convoluted on my Acer W500P tablet PC, because I have to press and hold Windows button and power button for a few seconds in order to use F2 to get into CMOS setup, or F12 to select boot order (to boot 64-bit 11.10 from internal USB connected SDHC).  Without a keyboard attached, it boots internal SSD (Win7) only, because there would be no way to hit F12 during boot.

---

### Post by spiky001 on 2012-01-02
where was grub loaded when you installed on the flash drive

---

### Post by user987 on 2012-01-02
**how do i find out where the grub is ?**

---

### Post by fdrake on 2012-01-02
> 
i have ubuntu 11.04 installed on a 16g flash drive and have been able to boot up my dell year 2009 netbook and run the netbook from the flash drive ubuntu os.

i tried the same flash drive on my year 2007 sony notebook and it does not work.

of course id doesn't work, it's not formatted to boot by itself but from grub, which mostly was installed in the hard-drive unless your default boot device in the Dell pc was the USB.

what you can do is plug the usb and boot the sony pc from a live cd of ubuntu and install grub either in the hard disk or in the USB (but you will have to keep the sub as default)

While using the live cd install Boot-Repair tool :[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
and follow the instructions at section "Reinstalling GRUB2" from this doc-page [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

If I were in you I would install the new grub in the USB without touching the hdd and windows! Just keep as default device the USB drive and you should be fine.

---

