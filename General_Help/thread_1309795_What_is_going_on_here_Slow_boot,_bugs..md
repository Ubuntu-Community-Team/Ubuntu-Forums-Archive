---
title: "What is going on here? Slow boot, bugs."
date: 2009-11-01
forum: General Help
---

### Post by pYrO1v1aniac on 2009-11-01
Having just upgraded to 9.10, boot and login takes quite a lot longer than usual, and displays kernel bugs.
_____________________________________________________
[   22.608115] Bridge firewalling registered
[   22.697252] phy1: Selected rate control algorithm 'minstrel'
[   22.697884] Registered led device: rt73usb-phy1::radio
[   22.697899] Registered led device: rt73usb-phy1::assoc
[   22.697912] Registered led device: rt73usb-phy1::quality
[   22.698434] usbcore: registered new interface driver rt73usb
[   22.819340] usb 3-1.2: USB disconnect, address 4
[   22.983340] usb 3-1.3: USB disconnect, address 5
[   23.585146] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 20 (level, low) -> IRQ 2
0
[   23.585177] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   23.632381] udev: renamed network interface wlan0 to wlan1
[   23.820033] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/inp
ut/input11
[   24.224682] cfg80211: World regulatory domain updated:
[   24.224685] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp
)
[   24.224688] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.224690] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.224692] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.224694] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.224696] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.055745] BUG: unable to handle kernel NULL pointer dereference at 00000040
[   25.055751] IP: [<c0484430>] apparmor_bprm_set_creds+0x370/0x400
[   25.055758] *pde = 00000000 
[   25.055761] Oops: 0000 [#1] SMP 
[   25.055763] last sysfs file: /sys/power/state
[   25.055766] Modules linked in: snd_hda_codec_realtek snd_hda_intel snd_hda_co
dec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_se
_______________________________________

[   26.007388] rt73usb 2-1:1.0: firmware: requesting rt73.bin
[   27.807060] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   29.401321] ip_tables: (C) 2000-2006 Netfilter Core Team
[   31.820904] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   31.821561] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   31.821743] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   31.821929] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   33.542621] ppdev: user-space parallel port driver
[   92.321905] wlan1: authenticate with AP 00:26:18:28:3e:80
[   92.323728] wlan1: authenticated
[   92.323731] wlan1: associate with AP 00:26:18:28:3e:80
[   92.327401] wlan1: RX AssocResp from 00:26:18:28:3e:80 (capab=0x411 status=0 aid=1)
[   92.327407] wlan1: associated
[   92.344851] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   93.625018] padlock: VIA PadLock not detected.
______________________________________

These are the strange sections I've taken from my boot dmesg

---

### Post by pYrO1v1aniac on 2009-11-01
Bump. Please help.

---

### Post by pYrO1v1aniac on 2009-11-01
Bump?

---

### Post by philinux on 2009-11-01
Install **bootchart** to get a clear picture of whats going on.

---

### Post by pYrO1v1aniac on 2009-11-01
This is what I have. 

100s seems pretty long. Anything I could do that you can see?

edit- Resolution is funny. I'll try again.

---

### Post by pYrO1v1aniac on 2009-11-01
Img now linked to photobucket.[http://i27.photobucket.com/albums/c191/pYrO1v1aniac/bootchart2.png]("http://i27.photobucket.com/albums/c191/pYrO1v1aniac/bootchart2.png")

---

### Post by philinux on 2009-11-01
I get 1.04. Are you running encrypted?

---

### Post by pYrO1v1aniac on 2009-11-01
No, I don't think so.

---

