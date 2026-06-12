---
title: "mouse problems in Maverick Meerkat"
date: 2011-02-11
forum: General Help
---

### Post by Akieboy on 2011-02-11
I am fairly new to Ubuntu, I am currently running Maverick Meerkat on an Acer Aspire 3690 laptop. I started having problems with the mouse in Lucid Lynx, it would just lock up, usually when I was looking at/working with graphics and/or on the web and I would have to hit ctrl+alt+f1 and then sudo service gdm restart and then it would work again for awhile at least.
I was unable to make any of the solutions in the forums work so I upgraded to maverick and that didn't help, I downloaded Maverick, made a startup disk on a usb key and did a clean install. It wasn't too bad at first but it is getting worse. I am having to restart 3 or 4 times a day. 
Might it help to do a complete new clean install?  Or does anyone have any other possible solutions.
I am adding to this that I have all the effects and extras shut off in Compiz and here is the log file just in case there is any info that can help. 
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   19.760383] Registered led device: b43-phy0::tx
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   19.760406] Registered led device: b43-phy0::rx
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   19.760433] Registered led device: b43-phy0::radio
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   19.760531] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   19.889324] type=1400 audit(1302416855.408:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=827 comm="apparmor_parser"
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   19.893551] type=1400 audit(1302416855.412:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=828 comm="apparmor_parser"
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   19.894377] type=1400 audit(1302416855.412:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=828 comm="apparmor_parser"
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   19.894831] type=1400 audit(1302416855.412:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=828 comm="apparmor_parser"
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   20.129112] type=1400 audit(1302416855.648:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=829 comm="apparmor_parser"
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   20.141137] type=1400 audit(1302416855.660:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=829 comm="apparmor_parser"
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   20.153917] type=1400 audit(1302416855.672:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=829 comm="apparmor_parser"
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   20.156138] Console: switching to colour frame buffer device 160x50
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   20.161883] fb0: inteldrmfb frame buffer device
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   20.161885] drm: registered panic notifier
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   20.167387] Slow work thread pool: Starting up
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   20.172172] Slow work thread pool: Ready
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   20.172192] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   20.172425] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   20.172489]   alloc irq_desc for 44 on node -1
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   20.172492]   alloc kstat_irqs on node -1
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   20.172508] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   20.172549] HDA Intel 0000:00:1b.0: setting latency timer to 64
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   20.240138] Skipping EDID probe due to cached edid
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   20.341406] hda_codec: ALC883: SKU not ready 0x411111f0
Apr 10 08:27:35 jerry-Aspire-3690 kernel: [   20.376937] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 10 08:27:36 jerry-Aspire-3690 kernel: [   20.606150] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000/0x0
Apr 10 08:27:36 jerry-Aspire-3690 kernel: [   20.628139] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
Apr 10 08:27:36 jerry-Aspire-3690 kernel: [   20.643762] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
Apr 10 08:27:36 jerry-Aspire-3690 kernel: [   20.675324] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 10 08:27:36 jerry-Aspire-3690 kernel: [   20.866541] ppdev: user-space parallel port driver
Apr 10 08:27:37 jerry-Aspire-3690 kernel: [   21.908183] Skipping EDID probe due to cached edid
Apr 10 08:27:37 jerry-Aspire-3690 kernel: [   22.260187] Skipping EDID probe due to cached edid
Apr 10 08:27:38 jerry-Aspire-3690 kernel: [   23.027561] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Apr 10 08:27:39 jerry-Aspire-3690 kernel: [   23.816206] b44 ssb1:0: eth0: Link is up at 100 Mbps, full duplex
Apr 10 08:27:39 jerry-Aspire-3690 kernel: [   23.816211] b44 ssb1:0: eth0: Flow control is off for TX and off for RX
Apr 10 08:27:39 jerry-Aspire-3690 kernel: [   23.816534] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr 10 08:27:39 jerry-Aspire-3690 kernel: [   24.212090] Skipping EDID probe due to cached edid
Apr 10 08:27:40 jerry-Aspire-3690 kernel: [   24.548078] Skipping EDID probe due to cached edid
Apr 10 08:27:40 jerry-Aspire-3690 kernel: [   24.876075] Skipping EDID probe due to cached edid
Apr 10 08:27:40 jerry-Aspire-3690 kernel: [   25.204061] Skipping EDID probe due to cached edid
Apr 10 08:27:41 jerry-Aspire-3690 kernel: [   25.764040] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Apr 10 08:27:47 jerry-Aspire-3690 kernel: [   31.492053] Skipping EDID probe due to cached edid
Apr 10 08:27:50 jerry-Aspire-3690 kernel: [   34.672017] eth0: no IPv6 routers present
Apr 10 08:44:37 jerry-Aspire-3690 kernel: [ 1042.289665] Skipping EDID probe due to cached edid
Apr 10 08:44:38 jerry-Aspire-3690 kernel: [ 1042.616105] Skipping EDID probe due to cached edid
Apr 10 08:44:39 jerry-Aspire-3690 kernel: [ 1043.780072] Skipping EDID probe due to cached edid
Apr 10 08:44:39 jerry-Aspire-3690 kernel: [ 1044.120081] Skipping EDID probe due to cached edid
Apr 10 08:44:39 jerry-Aspire-3690 kernel: [ 1044.448062] Skipping EDID probe due to cached edid
Apr 10 08:44:40 jerry-Aspire-3690 kernel: [ 1044.776061] Skipping EDID probe due to cached edid
Apr 10 08:44:46 jerry-Aspire-3690 kernel: [ 1050.716048] Skipping EDID probe due to cached edid

---

