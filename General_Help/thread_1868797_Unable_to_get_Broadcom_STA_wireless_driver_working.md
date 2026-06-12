---
title: "Unable to get Broadcom STA wireless driver working"
date: 2011-10-24
forum: General Help
---

### Post by Usernameisvalid on 2011-10-24
I have been unable to properly update my wireless network driver since upgrading from 11.04.  I had problems connecting in 11.04, but was able to get them resolved using a walk-through I found online.  I haven't been able to find that same walk-through, and other solutions I've come across haven't seemed to work.

I'm running Ubuntu 11.10 Oneiric Ocelot on my Dell Inspiron 1420.  It appears I have a Broadcom BCM4312 Network controller.

I'm very new to Ubuntu, and linux as a whole, and not very familiar with the layout of various setting panels, so please be thorough when directing me.  If I can do it entirely from the terminal, that would be great.

Many of the places I've come to in my search have recommended running the command:

lspci -vvnn | grep 14e4

to which I get:

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

If that helps at all.

Thanks in advance, and I'm happy to try any potential solution.

---

### Post by andied on 2011-10-24
I have a BCM4311 and could not get my wireless working with the auto installed third party driver (Broadcom STA). I fiddled with it for quite a while and finally installed Mint 11 - still wouldn't work.

I removed the third party driver and installed through Synaptic,  "b43-fwcutter", and "firmware b-43 installer" rebooted and it works. This is the "old way" and requires internet access to get the firmware.

It seems the driver is part of newer distributions with "bcmwl-kernel-source", but I could not get my card to work with this.

---

### Post by xianbei on 2011-10-24
assuming you've got a hard-wire connection to the internet, have you tried this:

```
sudo apt-get install firmware-b43-installer
```

?

---

### Post by Usernameisvalid on 2011-10-25
Both removing and reinstalling b43-fwcutter and the firmware for it doesn't seem to work. Doing the same with bcmwl-kernel-source didn't seem to help either.

Yes, I have a hard wire connection.

---

### Post by varunendra on 2011-10-27
> **Usernameisvalid said:**
> Both removing and reinstalling b43-fwcutter and the firmware for it doesn't seem to work. Doing the same with bcmwl-kernel-source didn't seem to help either.

Yes, I have a hard wire connection.
Try this first:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
sudo apt-get install firmware-b43-installer b43-fwcutter
sudo /etc/init.d/network-manager restart
```Also, make sure there is no 'blacklist-bcm43.conf' file in /etc/modprobe.d directory (delete it if there is) and there is no blacklist entry for b43 in '/etc/modprobe.d/blacklist.conf' file.


If the above does not help, please post outputs of:
```
lspci -nnk | grep -iA2 net
lsmod
cat /etc/modprobe.d/blacklist.conf | grep b43
```

---

### Post by Usernameisvalid on 2011-10-30
```
sudo etc/init.d/network-manager restart
```
Gave me a return of:
```
sudo: etc/init.d/network-manager: command not found
```
I checked for the blacklist-bcm43.conf file, it wasn't in there, and the only thing related to b43 in the blacklist.conf file was an entry that read
```
# replaced by b43 and ssb.
blacklist bcm43xx
```
----
Outputs:
lspci -nnk | grep -iA2 net
```
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
	Subsystem: Dell Inspiron 1420 [1028:01f3]
	Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Dell Wireless 1395 WLAN Mini-Card [1028:000b]
	Kernel driver in use: b43-pci-bridge
```

lsmod
```
Module                  Size  Used by
nls_utf8               12493  0 
isofs                  39549  0 
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
joydev                 17393  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_codec_idt      60049  1 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
arc4                   12473  2 
psmouse                73673  0 
serio_raw              12990  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
b43                   318816  0 
r852                   17901  0 
binfmt_misc            17292  1 
sm_common              16737  1 r852
nand                   49707  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
mtd                    35852  2 sm_common,nand
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              272785  1 b43
cfg80211              172392  2 b43,mac80211
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
wmi                    18744  1 dell_wmi
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  505108  3 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
ahci                   21634  2 
libahci                25727  1 ahci
tg3                   132972  0 
ssb                    50682  1 b43
```


cat /etc/modprobe.d/blacklist.conf | grep b43
```
# replaced by b43 and ssb.
```

---

### Post by varunendra on 2011-10-31
Sorry, that "network-manager restart" command was mistyped. There shouls have been a '/' before 'etc/....' I have corrected my previous post accordingly.

But anyway, it should have been automatically implemented with a system restart. So have you tried to connect after a system restart?

If it is still unable to connect, please post outputs of:
```
sudo lshw -C network
ifconfig -a
iwconfig
iwlist scan
rfkill list all
cat /etc/network/interfaces
```

---

### Post by Usernameisvalid on 2011-10-31
Still getting the "searching for connection" animation, followed by "Wireless network: Disconnected" after a while.  I can see all the networks in the area, and the one I'm trying to connect to is at full strength for signal power.
-----
Outputs:

sudo lshw -C network
```
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e1:07:aa:e5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:fd:f8:3b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 duplex=full firmware=sb v3.04 ip=192.168.1.66 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:47 memory:fe5f0000-fe5fffff
```

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:1c:23:fd:f8:3b  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fefd:f83b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5872 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7623868 (7.6 MB)  TX bytes:591217 (591.2 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1f:e1:07:aa:e5  
          inet6 addr: fe80::21f:e1ff:fe07:aae5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:18678
          TX packets:0 errors:29 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12128 (12.1 KB)  TX bytes:12128 (12.1 KB)
```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
```

iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.
```

rfkill list all
```
0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

cat /etc/network/interfaces
```
auto lo
iface lo inet loopback
```

---

