---
title: "Wireless Internet Problem"
date: 2011-08-26
forum: General Help
---

### Post by MSTRZ on 2011-08-26
Hello, MSTRZ here. This is my third ever thread, the previous two having been answered by two friendly gentlemen, and I'd like to keep that pattern going. (Ladies, feel free to help me out too :P)

I recently did a full wipe/install of Ubuntu 11.04 Natty Narwhal, and my WiFi Internet support is nil. Nonexistent. Strange thing is, it works on my brother's laptop, which is running the exact same version, set up with the exact same configuration. I just left-click on my brother's Internet icon, and boom, there's our Internet, ready to be connected to.

Is there something I'm doing wrong on MY laptop? I have not changed any settings or preferences, the Internet is simply not there. I know that my laptop has wireless internet capability, I used it for five years before I switched to Ubuntu. Our Internet is not hidden or anything like that, it just requires a password, which I know. The only things I'm doing differently on my laptop is the fact that I have the options 'nomodeset' and 'acpi=off' enabled, both of which are required for me to boot.

Any ideas?

Greatly appreciated,

MSTRZ

---

### Post by hasardeur on 2011-08-26
Hi, if you click on the Network-Manager is there a list of detected networks? On most boxes you should see the section for the wired connection and below that the wireless networks surrounding you.
Keep in mind that you need the passkey to actually access the connection - which in turn you must enter at least once.

---

### Post by Monotoko on 2011-08-26
Hi MSTRZ,

Please post the output of
```
sudo lspci
``` 
which will tell us what wifi card you have in the computer :)

---

### Post by timlev on 2011-08-26
You might also try the hardware wireless switch, which is often (Fn + F2).

---

### Post by MSTRZ on 2011-08-26
No, there is no list of detected networks.

Okay:

00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
08:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

Was the output.

Sorry, fn+f2 didn't work...


EDIT:
Ohh, scratch that, I DO have some additional configurations.
I have to boot up Ubuntu with both the 'nomodeset' and 'acpi=off' options enabled, otherwise it just hangs there at the purple boot-screen.
Acpi=off would explain why I have no battery symbol, huh?

---

### Post by MSTRZ on 2011-08-26
Uh...Hello? D:

---

### Post by samh25 on 2011-08-26
Hi guys new to the site and ubuntu.
i had problems once ubuntu was installed with my wireless.
This is what i did to get it up and running. I dont know if it will work for you but it work for me,

[LIST]
[*]Turn your modem off
[*]Disconnect your Ethernet cable from your wireless device
[*]Plug Ethernet cable into your laptop.
[*]Turn on modem and wait for it to set it safe to the laptop.
[*]Once connected got to ubuntu software centre and update all files.
[*]Go to system settings/ additional drivers/ and activate broadcom STA proprietary wireless driver.
[*]Ubuntu will then tell you to restart for changes to take effect.
[*]When ubuntu is restarting, disconnect the Ethernet cable and plug it back into your wireless device
[*]Turn modem off, wait a few seconds and turn it back on again.
[*]You should now be able to connect to hidden wireless networks [ yours should be in there ]
[/LIST]
if i done this completely wrong, let me know, still trying to work it out

---

### Post by MSTRZ on 2011-08-26
> **samh25 said:**
> Hi guys new to the site and ubuntu.
i had problems once ubuntu was installed with my wireless.
This is what i did to get it up and running. I dont know if it will work for you but it work for me,

[LIST]
[*]Turn your modem off
[*]Disconnect your Ethernet cable from your wireless device
[*]Plug Ethernet cable into your laptop.
[*]Turn on modem and wait for it to set it safe to the laptop.
[*]Once connected got to ubuntu software centre and update all files.
[*]Go to system settings/ additional drivers/ and activate broadcom STA proprietary wireless driver.
[*]Ubuntu will then tell you to restart for changes to take effect.
[*]When ubuntu is restarting, disconnect the Ethernet cable and plug it back into your wireless device
[*]Turn modem off, wait a few seconds and turn it back on again.
[*]You should now be able to connect to hidden wireless networks [ yours should be in there ]
[/LIST]
if i done this completely wrong, let me know, still trying to work it out

Thanks, I'll try this as soon as my father gets home.

---

