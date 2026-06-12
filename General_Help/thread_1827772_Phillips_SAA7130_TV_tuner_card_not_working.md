---
title: "Phillips SAA7130 TV tuner card not working"
date: 2011-08-18
forum: General Help
---

### Post by ukmad on 2011-08-18
I have tried all the web help [http://www.gentoo-wiki.info/SAA7134](http://www.gentoo-wiki.info/SAA7134) but still can't view on Ubuntu works fine on Windows.
Some output which could help you:
[   11.269072] tuner-simple 1-0060: type set to 37 (LG PAL (newer TAPC series)) 
[   11.375732] type=1505 audit(1313058682.363:7):  operation="profile_replace" pid=699 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
[   11.376183] type=1505 audit(1313058682.367:8):  operation="profile_replace" pid=699 name="/usr/lib/connman/scripts/dhclient-script" 
[   11.389261] saa7130[0]: registered device video0 [v4l2] 
[   11.389323] saa7130[0]: registered device vbi0 
[   11.389376] saa7130[0]: registered device radio0 
[   11.408369] type=1505 audit(1313058682.399:9):  operation="profile_load" pid=702 name="/usr/bin/evince" 
[   11.415983] saa7134 ALSA driver for DMA sound loaded 
[   11.415991] saa7130[0]/alsa: LifeView/Typhoon FlyVIDEO2000 doesn't support digital audio 


dmesg:
 [   10.943726] saa7130[0]: subsystem: 1131:0000, board: LifeView/Typhoon FlyVIDEO2000 [card=3,insmod option] 
[   10.943753] saa7130[0]: board init: gpio is 4000 
[   10.943759] saa7130[0]: there are different flyvideo cards with different tuners 
[   10.943761] saa7130[0]: out there, you might have to use the tuner=<nr> insmod 
[   10.943763] saa7130[0]: option to override the default value. 
[   10.943982] input: saa7134 IR (LifeView/Typhoon Fl as /devices/pci0000:00/0000:00:1e.0/0000:01:01.0/input/input4 
[   10.944178] IRQ 20/saa7130[0]: IRQF_DISABLED is not guaranteed on shared IRQs 
[   11.053642] saa7130[0]: Huh, no eeprom present (err=-5)? 
[   11.053649] i2c i2c-1: Invalid 7-bit address 0x7a 
[   11.073437] fb0: inteldrmfb frame buffer device 
[   11.073443] registered panic notifier 
[   11.073457] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0 
[   11.093894] vga16fb: initializing 
[   11.093902] vga16fb: mapped to 0xc00a0000 
[   11.093909] vga16fb: not registering due to another framebuffer present 
[   11.120937]   alloc irq_desc for 17 on node -1 
[   11.120943]   alloc kstat_irqs on node -1 
[   11.120957] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[   11.121030] Intel ICH 0000:00:1e.2: setting latency timer to 64 
[   11.204035] All bytes are equal. It is not a TEA5767 
[   11.204138] tuner 1-0060: chip found @ 0xc0 (saa7130[0]) 
[   11.220046] tuner-simple 1-0060: creating new instance 
[   11.220051] tuner-simple 1-0060: type set to 37 (LG PAL (newer TAPC series)) 
[   11.232474] Console: switching to colour frame buffer device 128x48 
[   11.248174] saa7130[0]: registered device video0 [v4l2] 
[   11.248242] saa7130[0]: registered device vbi0 
[   11.248310] saa7130[0]: registered device radio0 
[   11.256206] saa7134 ALSA driver for DMA sound loaded 
[   11.256214] saa7130[0]/alsa: LifeView/Typhoon FlyVIDEO2000 doesn't support digital audio





I have tried all options with different cards and tuners but nothing works except on some occasion where Composite 2 one channel is seen. What can I do I desperately need to make the TV live. I have TV time installed.

---

### Post by Mze on 2011-08-18
Try this [tutorial]("http://sites.google.com/site/jobinau2/saa7130basedtvtunercardunderlinux")..

---

