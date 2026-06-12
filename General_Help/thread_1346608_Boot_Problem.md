---
title: "Boot Problem"
date: 2009-12-05
forum: General Help
---

### Post by moltkestr19 on 2009-12-05
This happens since yesterday. On my laptop (aspire 4720z) ubuntu karmic boots very slow. dmesg shows something suspicious.

```
[    5.884633] PM: Starting manual resume from disk
[    5.884638] PM: Resume from partition 8:5
[    5.884640] PM: Checking hibernation image.
[    5.884841] PM: Resume from disk failed.
[    5.919914] kjournald starting.  Commit interval 5 seconds
[    5.919936] EXT3-fs: mounted filesystem with writeback data mode.
[    7.291038] type=1505 audit(1259940649.680:2): operation="profile_load" pid=427 name=/usr/share/gdm/guest-session/Xsession
[    7.335938] type=1505 audit(1259940649.720:3): operation="profile_load" pid=428 name=/sbin/dhclient3
[    7.336724] type=1505 audit(1259940649.720:4): operation="profile_load" pid=428 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    7.337151] type=1505 audit(1259940649.720:5): operation="profile_load" pid=428 name=/usr/lib/connman/scripts/dhclient-script
[    7.529182] type=1505 audit(1259940649.910:6): operation="profile_load" pid=429 name=/usr/bin/evince
[    7.542112] type=1505 audit(1259940649.930:7): operation="profile_load" pid=429 name=/usr/bin/evince-previewer
[    7.549673] type=1505 audit(1259940649.930:8): operation="profile_load" pid=429 name=/usr/bin/evince-thumbnailer
[    7.584343] type=1505 audit(1259940649.970:9): operation="profile_load" pid=431 name=/usr/lib/cups/backend/cups-pdf
[    7.585263] type=1505 audit(1259940649.970:10): operation="profile_load" pid=431 name=/usr/sbin/cupsd
[    7.618754] type=1505 audit(1259940650.000:11): operation="profile_load" pid=432 name=/usr/sbin/mysqld
[  364.591020] udev: starting version 147
[  364.680363] lp: driver loaded but no devices found
[  364.707386] Adding 1469908k swap on /dev/sda5.  Priority:-1 extents:1 across:1469908k 
[  366.128907] lib80211: common routines for IEEE802.11 drivers
[  366.128912] lib80211_crypt: registered algorithm 'NULL'
[  366.134010] wl: module license 'MIXED/Proprietary' taints kernel.
[  366.134019] Disabling lock debugging due to kernel taint
[  366.159368] ricoh-mmc: Ricoh MMC Controller disabling driver
[  366.159372] ricoh-mmc: Copyright(c) Philip Langdale
[  366.164569] sdhci: Secure Digital Host Controller Interface driver
[  366.164573] sdhci: Copyright(c) Pierre Ossman
[  366.205505] acer-wmi: Acer Laptop ACPI-WMI Extras
[  366.206039] acer-wmi: Brightness must be controlled by generic video driver
[  366.222379] wl 0000:04:00.0: enabling device (0000 -> 0002)
[  366.222393] wl 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  366.222413] wl 0000:04:00.0: setting latency timer to 64
[  366.241337] ricoh-mmc: Ricoh MMC controller found at 0000:0a:09.2 [1180:0843] (rev 12)
[  366.241366] ricoh-mmc: Controller is now disabled.
[  366.270305] sdhci-pci 0000:0a:09.1: SDHCI controller found [1180:0822] (rev 22)
[  366.270332] sdhci-pci 0000:0a:09.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[  366.271385] sdhci-pci 0000:0a:09.1: Will use DMA mode even though HW doesn't fully claim to support it.
[  366.272484] Registered led device: mmc0::
[  366.273542] mmc0: SDHCI controller on PCI [0000:0a:09.1] using DMA
[  366.276050] ------------[ cut here ]------------

```

As you can see, my laptop seems to do nothing between seconds 7.618754 and 364.591020. In this timespan, there seems to be a lot of disk activity. At first I thought it is the e2fsck, so i tried to disable it from grub, but no luck. Then I thought it is because apparmor, tried to disable it but again no luck.

I'm running out of ideas here. Any help will be appreciated. Thanks.

---

### Post by audiomick on 2009-12-05
Hallo.
Got no idea really, but:
The word "audit" is the english word for "Steuerprüfung", that is to say, checking something.
At a _**geuss**_, the boot up is having trouble checking something to do with a profile for mysql.

Do you live in Heilbronn?

---

### Post by moltkestr19 on 2009-12-05
> **audiomick said:**
> Hallo.
Got no idea really, but:
The word "audit" is the english word for "Steuerprüfung", that is to say, checking something.
At a _**geuss**_, the boot up is having trouble checking something to do with a profile for mysql.

Do you live in Heilbronn?

indeed. it loads apparmor profiles, and one of them is the one for mysql. i tried to disable it, but it has no effect at all. so i think it is not a problem with apparmor. i'm starting to think that the hard disk is problematic but have no idea how to check it since i can work normally after i logged in.

nah, i'm in hannover.

---

### Post by audiomick on 2009-12-06
fsck (look at the man page) will check your file system. From what I have read, the best way to check the disc itself is to read out the smart chip on the disc itself, which is what the manufacturers test program does. There are linux apps to do this, but I have forgotten what they are.

---

### Post by hoosierchick on 2009-12-18
I have the same issue.  I have found a pxe.img and some very BIZZARE items on my disk.  I personally think that this system is hacked.  

My firewall (firestarter) doesn't want to start on boot --  I have found several python 2.6 scripts that don't look good either. 

Any suggestions or if you want some logs -- I'll provide.

---

### Post by coffeeandlinux on 2009-12-18
Do you allow network activity (Ethernet or wireless) while the laptop is booting?

---

### Post by joes7 on 2009-12-18
I would re-install GRUB from the LiveCD.

---

### Post by hoosierchick on 2009-12-19
The profile errors he was getting and I am getting makes me think that somehow, my profiles are being "replaced".

---

