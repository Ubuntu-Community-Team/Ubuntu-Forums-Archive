---
title: "Multimedia Card Reader problem"
date: 2010-02-25
forum: General Help
---

### Post by weissnich on 2010-02-25
Hi,

my multimedia card reader does not work with new ubuntu version fresh install:

lsusb says:```
Bus 001 Device 002: alcor micro corp. multimedia card reader
```

dmesg:
```
[    6.544269] usb-storage: device scan complete
[    6.544848] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    6.545482] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    6.546102] scsi 2:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    6.546728] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    6.547227] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    6.547338] sd 2:0:0:1: Attached scsi generic sg3 type 0
[    6.547439] sd 2:0:0:2: Attached scsi generic sg4 type 0
[    6.547550] sd 2:0:0:3: Attached scsi generic sg5 type 0
[    6.549692] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[    6.550942] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    6.551564] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[    6.552191] sd 2:0:0:3: [sde] Attached SCSI removable disk
[   14.070641] udev: starting version 147
[   14.093423] Adding 3911788k swap on /dev/sda6.  Priority:-1 extents:1 across:3911788k 
[   14.104764] lp: driver loaded but no devices found
[   14.108576] intel_rng: FWH not detected
[   14.167506] EXT4-fs (sda5): internal journal on sda5:8
[   14.301752] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.336542] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   14.336771] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   14.336774] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   14.336777] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   14.365231] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   14.788234] r8169: eth0: link up
[   14.788243] r8169: eth0: link up
[   16.023586] ppdev: user-space parallel port driver
[   16.833711] CPU0 attaching NULL sched-domain.
[   16.833717] CPU1 attaching NULL sched-domain.
[   16.844631] CPU0 attaching sched-domain:
[   16.844638]  domain 0: span 0-1 level MC
[   16.844644]   groups: 0 1
[   16.844652]   domain 1: span 0-1 level CPU
[   16.844658]    groups: 0-1 (__cpu_power = 2048)
[   16.844668] CPU1 attaching sched-domain:
[   16.844673]  domain 0: span 0-1 level MC
[   16.844678]   groups: 1 0
[   16.844685]   domain 1: span 0-1 level CPU
[   16.844690]    groups: 0-1 (__cpu_power = 2048)
[   17.508553] i2c-adapter i2c-1: unable to read EDID block.
[   17.508558] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   17.512964] i2c-adapter i2c-1: unable to read EDID block.
[   17.512966] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   17.761040] i2c-adapter i2c-1: unable to read EDID block.
[   17.761044] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   17.765452] i2c-adapter i2c-1: unable to read EDID block.
[   17.765455] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   25.116014] eth0: no IPv6 routers present
[   32.116706] i2c-adapter i2c-1: unable to read EDID block.
[   32.116711] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   32.121488] i2c-adapter i2c-1: unable to read EDID block.
[   32.121494] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   32.368513] i2c-adapter i2c-1: unable to read EDID block.
[   32.368518] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   32.372925] i2c-adapter i2c-1: unable to read EDID block.
[   32.372927] i915 0000:00:02.0: HDMI Type A-1: no EDID data

```

---

### Post by dabl on 2010-02-25
It's not obvious from your dmesg that it is not being seen correctly.  What happens when you put a formatted card in it?

---

### Post by Merovius on 2010-02-26
Same problem on HP desktop. Built in reader does not mount. It is seen.

---

