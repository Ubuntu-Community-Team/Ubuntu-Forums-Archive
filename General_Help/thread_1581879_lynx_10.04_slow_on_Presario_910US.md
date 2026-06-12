---
title: "lynx 10.04 slow on Presario 910US"
date: 2010-09-25
forum: General Help
---

### Post by telecomtom on 2010-09-25
i've used ubuntu on my Compaq Presario 910US laptop (with 1GB RAM) for several years. no problems. but when i installed lynx 10.04 LTS last week it ran / responded very slowly. has anyone had a similar problem? is there some kind of setting that i need to change?

---

### Post by 666f6f on 2010-09-25
Hello,

I suspect that the problem is the graphics adapter. Can you post the output of ```
sudo lspci
```?

---

### Post by telecomtom on 2010-09-25
> **666f6f said:**
> Hello,

I suspect that the problem is the graphics adapter. Can you post the output of ```
sudo lspci
```?

sure:

00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 20)
00:0c.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:13.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1

please note: i'm temporarily running debian on the laptop, but i assume the output of lspci is the same as it would be for ubuntu. if that's not the case, let me know and i'll boot back into ubuntu and run the command.

---

### Post by 666f6f on 2010-09-25
The output of the lspci command is the same. However, I'm not very optimist that the "ATI Technologies Inc Radeon Mobility U1" will play very nicely.

We can try however to force set the Xorg radeon driver with the following commands.

```
 
sudo mv /etc/X11/xorg.config /etc/X11/xorg.config # Backup existing xorg.conf.
cd /etc/X11/ && sudo Xorg -configure # Generate new xorg.conf.
sudo sed -i 's/Driver\s*"[^"]*"/Driver "radeon"/ig' /etc/xorg.conf # Replace detected driver with radeon driver.

```

Reboot your system and keep your fingers crossed!

---

### Post by telecomtom on 2010-09-27
> **666f6f said:**
> The output of the lspci command is the same. However, I'm not very optimist that the "ATI Technologies Inc Radeon Mobility U1" will play very nicely.

We can try however to force set the Xorg radeon driver with the following commands.

```
 
sudo mv /etc/X11/xorg.config /etc/X11/xorg.config # Backup existing xorg.conf.
cd /etc/X11/ && sudo Xorg -configure # Generate new xorg.conf.
sudo sed -i 's/Driver\s*"[^"]*"/Driver "radeon"/ig' /etc/xorg.conf # Replace detected driver with radeon driver.

```

Reboot your system and keep your fingers crossed!

i think i must have messed up the editing command (sed) because the network somehow got disabled, and no change to the slow display. 

i've been looking at some of the X features of 10.04 and 8.04 and it looks complicated. i think i'll have to go back to debian for a while till i get this figured out.

thanks for the suggestions.

---

