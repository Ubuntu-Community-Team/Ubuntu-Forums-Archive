---
title: "USB drive not being recognized"
date: 2009-11-30
forum: General Help
---

### Post by wrathican on 2009-11-30
Hi people,
I'm having yrouble mounting my USB drive and wondered if anyone could help?

if i run dmesg | tail -50 this is what i get:
```
[   30.122537] hub 1-0:1.0: unable to enumerate USB device on port 1
[   30.780036] usb 2-1: new full speed USB device using ohci_hcd and address 3
[   30.988043] usb 2-1: not running at top speed; connect to a high speed hub
[   31.003919] usb 2-1: configuration #1 chosen from 1 choice
[   31.210870] usb 2-1: reset full speed USB device using ohci_hcd and address 3
[   31.432844] phy0: Selected rate control algorithm 'minstrel'
[   31.433778] zd1211rw 2-1:1.0: phy0
[   31.495641] usb 2-1: firmware: requesting zd1211/zd1211b_ub
[   31.510816] usb 2-1: firmware: requesting zd1211/zd1211b_uphr
[   31.748046] zd1211rw 2-1:1.0: firmware version 4725
[   31.808049] zd1211rw 2-1:1.0: zd1211b chip 050d:705c v4810 full 00-1c-df AL2230_RF pa0 g--N-
[   31.813052] cfg80211: Calling CRDA for country: US
[   31.815057] cfg80211: Regulatory domain changed to country: US
[   31.815061] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   31.815065] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   31.815068] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   31.815071] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   31.815074] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   31.815077] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   31.911685] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.741151] wlan0: authenticate with AP 00:1b:2f:96:04:fe
[   40.744051] wlan0: authenticated
[   40.744055] wlan0: associate with AP 00:1b:2f:96:04:fe
[   40.747050] wlan0: RX AssocResp from 00:1b:2f:96:04:fe (capab=0x431 status=0 aid=1)
[   40.747053] wlan0: associated
[   40.748082] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   51.270021] wlan0: no IPv6 routers present
[   88.412526] Clocksource tsc unstable (delta = -156185868 ns)
[  600.970039] usb 1-2: new high speed USB device using ehci_hcd and address 9
[  601.100038] usb 1-2: device descriptor read/64, error -71
[  601.340033] usb 1-2: device descriptor read/64, error -71
[  601.570037] usb 1-2: new high speed USB device using ehci_hcd and address 10
[  601.700031] usb 1-2: device descriptor read/64, error -71
[  601.940049] usb 1-2: device descriptor read/64, error -71
[  602.170036] usb 1-2: new high speed USB device using ehci_hcd and address 11
[  602.590035] usb 1-2: device not accepting address 11, error -71
[  602.712552] usb 1-2: new high speed USB device using ehci_hcd and address 12
[  603.130048] usb 1-2: device not accepting address 12, error -71
[  603.130072] hub 1-0:1.0: unable to enumerate USB device on port 2
[  603.670037] usb 2-2: new full speed USB device using ohci_hcd and address 4
[  603.850039] usb 2-2: device descriptor read/64, error -62
[  604.140033] usb 2-2: device descriptor read/64, error -62
[  604.432533] usb 2-2: new full speed USB device using ohci_hcd and address 5
[  604.630033] usb 2-2: device descriptor read/64, error -62
[  604.920039] usb 2-2: device descriptor read/64, error -62
[  605.210033] usb 2-2: new full speed USB device using ohci_hcd and address 6
[  605.632526] usb 2-2: device not accepting address 6, error -62
[  605.810049] usb 2-2: new full speed USB device using ohci_hcd and address 7
[  606.232525] usb 2-2: device not accepting address 7, error -62
[  606.232543] hub 2-0:1.0: unable to enumerate USB device on port 2

```

ive searched on google to no avail.
thanks in advanced
Ash

---

### Post by wilee-nilee on 2009-11-30
Have you had a look at it from gparted? If there is nothing on it you may just need to reformat it.

---

### Post by StuartN on 2009-11-30
> **wrathican said:**
> Hi people,
I'm having yrouble mounting my USB drive and wondered if anyone could help?

This thread - [http://www.linuxquestions.org/questions/linux-hardware-18/usb-error-usb-2-4-device-descriptor-read64-error-71-643022/](http://www.linuxquestions.org/questions/linux-hardware-18/usb-error-usb-2-4-device-descriptor-read64-error-71-643022/) - suggests that error 71 is a suspend problem that you can unblock like this:

"in the terminal type: echo -1 >/sys/module/usbcore/parameters/autosuspend"

---

### Post by wrathican on 2009-11-30
thanks for your advice both of you

The device doesn't show up in a gparted,
I tried your solution StuartN, but i got a permission denied error from bash, even running the command as root.
```
ashley@ashley-desktop:~$ sudo echo -1 >/sys/module/usbcore/parameters/autosuspend
bash: /sys/module/usbcore/parameters/autosuspend: Permission denied
ashley@ashley-desktop:~$ 

```

any ideas why i get the permission denied?
or any other fixes for my problems?

thanks again
Ash

---

### Post by StuartN on 2009-11-30
> **wrathican said:**
> any ideas why i get the permission denied?

It must be some protection afforded by the Ubuntu security model - the person who wrote that was logged in as root. So instead of **sudo echo -1 > ...**, you need to **sudo bash** and then **echo -1 > ...** within the root terminal that comes up. (I tried it and it allowed me to rewrite the parameter).

---

### Post by wilee-nilee on 2009-11-30
> **wrathican said:**
> thanks for your advice both of you
The device doesn't show up in a gparted,


If you choose the drop down top right corner in gparted it still doesn't show? Is this a HD or a thumb? and has it worked before? is it brand new?

---

### Post by Phalangees on 2009-12-02
I came across a very similar problem today. Instead of error 62 I get 110. Not sure if this is different enough to make another thread. My 2gb thumb drive does not show up in gparted and the solution mentioned by StuartN does not work. I hope it's not broken because it is fairly new.

Here is the tail end of dmesg starting when I plug in the drive:
```
[18200.792236] usb 1-2: new high speed USB device using ehci_hcd and address 43
[18200.927065] usb 1-2: configuration #1 chosen from 1 choice
[18200.929647] scsi12 : SCSI emulation for USB Mass Storage devices
[18200.933892] usb-storage: device found at 43
[18200.933907] usb-storage: waiting for device to settle before scanning
[18205.936354] usb-storage: device scan complete
[18206.048212] usb 1-2: reset high speed USB device using ehci_hcd and address 43
[18211.188216] usb 1-2: device descriptor read/all, error -110
[18211.300157] usb 1-2: reset high speed USB device using ehci_hcd and address 43
[18216.440358] usb 1-2: device descriptor read/all, error -110
[18216.552250] usb 1-2: reset high speed USB device using ehci_hcd and address 43
[18221.580225] usb 1-2: device descriptor read/all, error -110
[18221.692218] usb 1-2: reset high speed USB device using ehci_hcd and address 43
[18226.712239] usb 1-2: device descriptor read/all, error -110
[18226.712471] usb 1-2: USB disconnect, address 43
[18226.824191] usb 1-2: new high speed USB device using ehci_hcd and address 44
[18231.964232] usb 1-2: device descriptor read/all, error -110
[18232.076218] usb 1-2: new high speed USB device using ehci_hcd and address 45
[18237.216242] usb 1-2: device descriptor read/all, error -110
[18237.328133] usb 1-2: new high speed USB device using ehci_hcd and address 46
[18242.352244] usb 1-2: device descriptor read/all, error -110
[18242.464224] usb 1-2: new high speed USB device using ehci_hcd and address 47
[18247.488203] usb 1-2: device descriptor read/all, error -110
[18247.488248] hub 1-0:1.0: unable to enumerate USB device on port 2
[18247.756201] usb 2-2: new full speed USB device using uhci_hcd and address 6
[18252.898216] usb 2-2: device descriptor read/all, error -110
[18253.008207] usb 2-2: new full speed USB device using uhci_hcd and address 7
[18258.150194] usb 2-2: device descriptor read/all, error -110
[18258.260223] usb 2-2: new full speed USB device using uhci_hcd and address 8
[18263.290213] usb 2-2: device descriptor read/all, error -110
[18263.400193] usb 2-2: new full speed USB device using uhci_hcd and address 9
[18268.430195] usb 2-2: device descriptor read/all, error -110
[18268.430242] hub 2-0:1.0: unable to enumerate USB device on port 2

```

Thank you for any and all help you can provide.

---

