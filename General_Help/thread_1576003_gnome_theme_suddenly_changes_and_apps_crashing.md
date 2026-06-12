---
title: "gnome theme suddenly changes and apps crashing"
date: 2010-09-16
forum: General Help
---

### Post by axe87 on 2010-09-16
All of a sudden my gnome theme changed and various apps including thunderbird and firefox started crashing. I've traced the first occurrence back to the following errors, starting with a segmentation fault in canberra-gtk-pl in kern.log:

```
Sep 15 10:21:44 leonardo kernel: [   15.968258] [drm] Setting GART location based on new memory map
Sep 15 10:21:44 leonardo kernel: [   15.968344] [drm] Loading R300 Microcode
Sep 15 10:21:44 leonardo kernel: [   15.968350] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
Sep 15 10:21:44 leonardo kernel: [   15.973844] [drm] Num pipes: 2
Sep 15 10:21:44 leonardo kernel: [   15.973854] [drm] writeback test succeeded in 1 usecs
Sep 15 10:21:44 leonardo kernel: [   16.308206] usb 3-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
Sep 15 10:21:45 leonardo kernel: [   17.656342] __ratelimit: 9 callbacks suppressed
Sep 15 10:21:45 leonardo kernel: [   17.656349] canberra-gtk-pl[1520]: segfault at 814e ip 0000814e sp bfe2d9cc error 4 in libgmodule-2.0.so.0.2400.1[110000+3000]
Sep 15 10:21:50 leonardo kernel: [   22.540078] wlan0: deauthenticating from 00:26:4d:77:8f:77 by local choice (reason=3)
Sep 15 10:21:50 leonardo kernel: [   22.541298] wlan0: direct probe to AP 00:26:4d:77:8f:77 (try 1)
Sep 15 10:21:50 leonardo kernel: [   22.543076] wlan0: direct probe responded
Sep 15 10:21:50 leonardo kernel: [   22.543080] wlan0: authenticate with AP 00:26:4d:77:8f:77 (try 1)
Sep 15 10:21:50 leonardo kernel: [   22.544937] wlan0: authenticated
Sep 15 10:21:50 leonardo kernel: [   22.544973] wlan0: associate with AP 00:26:4d:77:8f:77 (try 1)
Sep 15 10:21:50 leonardo kernel: [   22.547086] wlan0: RX AssocResp from 00:26:4d:77:8f:77 (capab=0x431 status=0 aid=1)
Sep 15 10:21:50 leonardo kernel: [   22.547091] wlan0: associated
Sep 15 10:21:50 leonardo kernel: [   22.547759] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Sep 15 10:21:50 leonardo kernel: [   22.547830] cfg80211: Calling CRDA for country: DE
Sep 15 10:21:50 leonardo kernel: [   22.558263] cfg80211: Received country IE:
Sep 15 10:21:50 leonardo kernel: [   22.558268] cfg80211: Regulatory domain: DE
Sep 15 10:21:50 leonardo kernel: [   22.558270]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep 15 10:21:50 leonardo kernel: [   22.558273]     (2402000 KHz - 2494000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
Sep 15 10:21:50 leonardo kernel: [   22.558275] cfg80211: CRDA thinks this should applied:
Sep 15 10:21:50 leonardo kernel: [   22.558277] cfg80211: Regulatory domain: DE
Sep 15 10:21:50 leonardo kernel: [   22.558279]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep 15 10:21:50 leonardo kernel: [   22.558282]     (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
Sep 15 10:21:50 leonardo kernel: [   22.558284]     (5150000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Sep 15 10:21:50 leonardo kernel: [   22.558287]     (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
Sep 15 10:21:50 leonardo kernel: [   22.558289] cfg80211: We intersect both of these and get:
Sep 15 10:21:50 leonardo kernel: [   22.558291] cfg80211: Regulatory domain: 98
Sep 15 10:21:50 leonardo kernel: [   22.558292]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep 15 10:21:50 leonardo kernel: [   22.558295]     (2402000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
Sep 15 10:21:50 leonardo kernel: [   22.558302] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
Sep 15 10:21:50 leonardo kernel: [   22.558307] cfg80211: Current regulatory domain updated by AP to: DE
Sep 15 10:21:50 leonardo kernel: [   22.558309]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep 15 10:21:50 leonardo kernel: [   22.558311]     (2402000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
Sep 15 10:21:50 leonardo kernel: [   22.581092] padlock: VIA PadLock not detected.
Sep 15 10:21:59 leonardo kernel: [   32.864008] wlan0: no IPv6 routers present
Sep 15 10:22:03 leonardo kernel: [   36.517514] gnome-settings-[1781]: segfault at 86ce ip 000086ce sp bf96038c error 4 in libgobject-2.0.so.0.2400.1[110000+3d000]
Sep 15 10:22:03 leonardo kernel: [   36.757689] canberra-gtk-pl[1782]: segfault at 814e ip 0000814e sp bfc43a4c error 4 in libpangoft2-1.0.so.0.2800.0[110000+25000]
Sep 15 10:22:42 leonardo kernel: [   75.824171] ondemand governor failed, too long transition latency of HW, fallback to performance governor
Sep 15 10:23:26 leonardo kernel: [  120.066160] b43legacy-phy0 ERROR: PHY transmission error
Sep 15 10:23:39 leonardo kernel: [  132.402023] gnome-panel[1788]: segfault at 814e ip 0000814e sp bfee5dac error 4 in libcanberra.so.0.2.1[110000+e000]
Sep 15 10:23:45 leonardo kernel: [  139.065151] b43legacy-phy0 ERROR: PHY transmission error
Sep 15 10:24:03 leonardo kernel: [  157.043155] gnome-panel[2020]: segfault at 814e ip 0000814e sp bfbd880c error 4 in libgdk_pixbuf-2.0.so.0.2000.1[110000+18000]
Sep 15 10:24:28 leonardo kernel: [  181.384799] gnome-panel[2097]: segfault at 814e ip 0000814e sp bf8854ec error 4 in libORBit-2.so.0.1.0[110000+49000]
Sep 15 10:24:35 leonardo kernel: [  188.631675] gnome-panel[2170]: segfault at 814e ip 0000814e sp bfa4fb5c error 4 in libgnome-desktop-2.so.17.1.0[110000+25000]
Sep 15 10:24:51 leonardo kernel: [  204.377846] gnome-panel[2223]: segfault at 814e ip 0000814e sp bfc48e4c error 4 in libdbus-glib-1.so.2.1.0[110000+1c000]
Sep 15 10:24:58 leonardo kernel: [  211.795801] gnome-panel[2284]: segfault at 814e ip 0000814e sp bff0509c error 4 in libbonobo-2.so.0.0.0[110000+51000]
Sep 15 10:25:17 leonardo kernel: [  230.713817] gnome-panel[2324]: segfault at 814e ip 0000814e sp bf99678c error 4 in libbonoboui-2.so.0.0.0[110000+5a000]
Sep 15 10:25:22 leonardo kernel: [  235.848695] gnome-panel[2398]: segfault at 814e ip 0000814e sp bfa718bc error 4 in libbonobo-2.so.0.0.0[110000+51000]
Sep 15 10:25:27 leonardo kernel: [  241.147603] gnome-panel[2436]: segfault at 814e ip 0000814e sp bfa2685c error 4 in libgdk-x11-2.0.so.0.2000.1[110000+93000]
Sep 15 10:25:49 leonardo kernel: [  263.225889] gnome-panel[2473]: segfault at 814e ip 0000814e sp bfa3908c error 
```

I'm assuming the wifi errors are nothing to do with it.

As I'd just made the switch to ubuntu and now can't use e-mail I'm stuck until I can get this fixed. Any ideas appreciated.

---

### Post by axe87 on 2010-09-17
Problem solved...the culprit was squeezeplay which I recently installed. Uninstalled it and everything is back to normal. The strange thing was, why did this not show up immediately after I installed and rebooted?

---

