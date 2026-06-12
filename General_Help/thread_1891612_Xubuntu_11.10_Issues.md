---
title: "Xubuntu 11.10 Issues"
date: 2011-12-06
forum: General Help
---

### Post by anirbanghosh on 2011-12-06
1. How to set the startup brightness in xubuntu 11.10 for my Dell Studio 15 Laptop?
2. Is there any world clock application for the panel?

---

### Post by DapperMe17 on 2011-12-06
Your screen brightness can be controlled via the F keys....sometimes f2 & f3 on laptops. Set it where you want it, and when you log out, your system state will be saved for the next log in

For a world clock panel applet....search the repos for "xfce4-" and look for related panel plugins

---

### Post by anirbanghosh on 2011-12-06
Sorry brightness issue is not resolved. Any further help please?

---

### Post by Toz on 2011-12-06
What video card do you have and which driver are you using? 
```
sudo lspci | grep -A 10 VGA
```

Have you tried the **acpi_backlight=vendor** kernel parameter?

---

### Post by anirbanghosh on 2011-12-06
The command says the following.

```
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500/5100 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
04:00.0 Network controller: Intel Corporation WiFi Link 5100
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
```

---

### Post by Toz on 2011-12-06
Sorry, I meant:
```
sudo lspci -vnn | grep -A 10 VGA
```

Are you using the proprietary ati video drivers?

And while your at it, what backlight interfaces do you have?
```
cat /sys/class/backlight
```

Was using the **acpi_backlight=vendor** kernel parameter helpful? Instructions on how to test it can be found at: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot")

---

### Post by BlakJakNZ on 2012-04-02
> **DapperMe17 said:**
> Your screen brightness can be controlled via the F keys....sometimes f2 & f3 on laptops. Set it where you want it, and when you log out, your system state will be saved for the next log in

For a world clock panel applet....search the repos for "xfce4-" and look for related panel plugins


I'd been looking for a world clock too.
A search for xfce4- gave me 'Orage Globaltime' which was already shown as installed.

I called 'orage' from a shell which opened up the calendar applet but as an application.
From the view menu click on 'Show Globaltime'.
This is a world clock tool.

Once set up you can run it by simply calling 'globaltime' (found in /usr/bin).

Hope this is of some help. (My experience is from Xubuntu 12.04 which is still beta).
The Panel clock isn't anywhere near as useful as the one from Ubuntu which did let you load multiple clocks easily enough.

---

