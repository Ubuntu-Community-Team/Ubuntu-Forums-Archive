---
title: "Partition Missing and No Wifi with 11.04"
date: 2011-10-11
forum: General Help
---

### Post by DeathByLinux on 2011-10-11
Hello,
        I installed 11.04 yesterday and all was working well for the first 6 or so hours but then suddenly I got disconnected from my wifi and could not connect to it again. I thought it was strange and so I decided to reboot and discovered that A) with the wireless enabled, I could not detect any wireless signals and B) the partition that I had created before upgrading was not visible any longer. 
Let me explain how I went about upgrading to perhaps reveal what the problem may be.
This is what the partitions looked like before I upgraded.
 
dev/sda1/swap
     /sda2/ext4
    /sda3/ext4 (home folder)
Then, I deleted the sda2, which was my system folder, and installed 11.04 in its stead. (I selected sda3, used the delete option, then used the unallocated space for the "/")
 
So, around 12am in the morning the wifi stopped working and the sda3 disappeared. I decided to go to bed and research the problem in the morning.
In the morning, I plugged in my live-USB and could see the sda3 from the live-boot, but the problem with the wifi presisted. I have it enabled, but it does not give me a list of networks to join as it normally does.
Thoughts?
-DeathbyLinux

---

### Post by DeathByLinux on 2011-10-11
No one can help? :( I am just going to go ahead and reinstall 11.04 again and see where that gets me. I may not have wifi still, so that seems to be the biggest problem.

---

### Post by Dangertux on 2011-10-12
Hey buddy -- sorry it took me so long to get around to this thread.

You kind of did the opposite of what we talked about, I thought /dev/sda3 was your home folder partition.

If you set the mount point for / to /dev/sda3 then that is where Ubuntu 11.04 installed to. I thought you decided you were going to keep your home partition?

In any case, if you want to use /dev/sda2 as your / partition and /dev/sda3 as your home partition you will have to reinstall with them in this configuration.  If not the extra partition will have to be defined with a mount point in order to have it mounted, if there is no mount point specified then it will not be allocated as anything other than free space.

I would recommend booting to a LiveCD and using Gparted to set your partitions up the way you originally wanted, possibly just doing another reinstall would be faster.

Hope that helps.

---

### Post by DeathByLinux on 2011-10-12
Okay, so I want to make that my home folder. So, when i click it it gives me several options for "use as": 
Ext4
Ext3
Ext2
ReiserF
Btrfs
XFS
FAT16 (Windows, i guess)
FAT32  (again Windows)
swap area (this is the RAM like area, right?)
do not use this partition (default)

Can you tell me under which of these options I make sda3 my home folder? A few of them offer to, but i don't know which one to pick it from.

---

### Post by wildmanne39 on 2011-10-12
Hi, I would create the partition as ext4 then below where you set it click on the drop down menu and choose the mount point as /home.
Thank you

---

### Post by DeathByLinux on 2011-10-12
Okay, 
         problem 1 solved. Wifi is still inactive. I have it enabled but I cannot see any networks from which to connect to the internet. I am actually typing from a computer that is connected to a network that is WELL within range of the computer that I am installing Linux on. What could the problem be?
Also, if it is a driver problem (bear with me, here. I know it may be ignorant), could I download the driver via my windows computer, put it on a USB and unzip it on my Linux computer?
Thanks for you guys' help. 
-DeathbyLinux

---

### Post by wildmanne39 on 2011-10-12
Hi, run these commands please so we can see if it is a driver problem and post the results here.
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.

You just copy and paste the commands into the terminal please, if you do not have a wired connection you can put the output on a flash drive then paste the output here.
Thank you

---

### Post by DeathByLinux on 2011-10-12
```

```test

---

### Post by DeathByLinux on 2011-10-13
```

cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux nav-Satellite-U400 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

``````
sudo lshw -C network
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 88E8040T PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 12
       serial: 00:1e:68:5d:c2:87
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:81000000-81003fff ioport:6000(size=256)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:9e:ef:5e:c8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:81400000-8140ffff
``````
lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller [11ab:4355] (rev 12)
    Subsystem: Toshiba America Info Systems Satellite P305D-S8995E [1179:ff50]
    Kernel driver in use: sky2
--
08:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7096]
    Kernel driver in use: ath5k
``````
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
``````
rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```



```
 lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
usb_storage            43946  1 
uas                    17676  0 
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_conexant    43782  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
uvcvideo               66851  0 
ath5k                 144412  0 
snd_rawmidi            25269  1 snd_seq_midi
videodev               75143  1 uvcvideo
i915                  450944  3 
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
cfg80211              156212  3 ath5k,ath,mac80211
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
lp                     13349  0 
soundcore              12600  1 snd
drm_kms_helper         40745  1 i915
serio_raw              12990  0 
drm                   180037  4 i915,drm_kms_helper
joydev                 17322  0 
sparse_keymap          13666  0 
parport                36746  3 parport_pc,ppdev,lp
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  3 
libahci                25548  1 ahci
firewire_ohci          31504  0 
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sky2                   49172  0 
```

---

### Post by wildmanne39 on 2011-10-13
Hi, give this a try please:
```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall linux-backports-modules-wireless-natty-generic
sudo apt-get update
sudo apt-get upgrade
sudo modprobe ath5k
```
Thank you

---

### Post by DeathByLinux on 2011-10-14
Hey Wildman,
                    I have tried a wired connection to run the commands you asked, but it doesn't even allow wired connection. It simply does not load. 
Yesterday, I got a friend to make me a boot disk for 11.10 and I was having the same issue with the wireless and I am guess the same with the wired if I tried it. 
Is there a way I could find the files that you want me to use, put them on a USB and use terminal to execute them?
-DeathbyLinux

---

### Post by wildmanne39 on 2011-10-15
Hi, you have the driver but I am not sure about the firmware, I tried to find away to put it on a usb but I am not that good at doing that and getting the correct code to install it.

Let&#347; run a few more commands and see if it sees networks and if there are any error messages, maybe we can get by with what you have, I did not know that you did not have a wired connection, or I may have forgot.

Please post the results of:
```
nm-tool
```
```
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wlan0 | tail -n25
```
Thank you

---

### Post by DeathByLinux on 2011-10-15
```
nm-tool


NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:1E:68:5D:C2:87

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:1B:9E:EF:5E:C8

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


```

```
sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

```

```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wlan0 | tail -n25
Oct 15 12:48:17 nav-Satellite-U400 NetworkManager[645]: <info> (wlan0): now unmanaged
Oct 15 12:48:17 nav-Satellite-U400 NetworkManager[645]: <info> (wlan0): device state change: 3 -> 1 (reason 37)
Oct 15 12:48:17 nav-Satellite-U400 NetworkManager[645]: <info> (wlan0): cleaning up...
Oct 15 12:48:17 nav-Satellite-U400 NetworkManager[645]: <info> (wlan0): taking down device.
Oct 15 12:48:29 nav-Satellite-U400 kernel: [ 5861.925932] ath5k 0000:08:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Oct 15 12:48:29 nav-Satellite-U400 kernel: [ 5861.925963] ath5k 0000:08:00.0: restoring config space at offset 0x4 (was 0x4, writing 0x81400004)
Oct 15 12:48:29 nav-Satellite-U400 kernel: [ 5861.925971] ath5k 0000:08:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Oct 15 12:48:29 nav-Satellite-U400 kernel: [ 5861.925981] ath5k 0000:08:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
Oct 15 12:48:29 nav-Satellite-U400 NetworkManager[645]: <info> (wlan0): now managed
Oct 15 12:48:29 nav-Satellite-U400 NetworkManager[645]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Oct 15 12:48:29 nav-Satellite-U400 NetworkManager[645]: <info> (wlan0): bringing up device.
Oct 15 12:48:29 nav-Satellite-U400 NetworkManager[645]: <info> (wlan0): preparing device.
Oct 15 12:48:29 nav-Satellite-U400 NetworkManager[645]: <info> (wlan0): deactivating device (reason: 2).
Oct 15 12:48:29 nav-Satellite-U400 kernel: [ 5864.067352] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 15 12:48:29 nav-Satellite-U400 NetworkManager[645]: <info> (wlan0): supplicant interface state:  starting -> ready
Oct 15 12:48:29 nav-Satellite-U400 NetworkManager[645]: <info> (wlan0): device state change: 2 -> 3 (reason 42)


```


Also, I found this one code that may help shed some light:

```
 lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at f0000000 (64-bit, non-prefetchable) [size=1M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, fast devsel, latency 0
    Memory at f0100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at f0704800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 80000000-801fffff
    Prefetchable memory behind bridge: 0000000080200000-00000000803fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 80400000-805fffff
    Prefetchable memory behind bridge: 0000000080600000-00000000807fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: 80800000-809fffff
    Prefetchable memory behind bridge: 0000000080a00000-0000000080bfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: 80c00000-80dfffff
    Prefetchable memory behind bridge: 0000000080e00000-0000000080ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: 81000000-811fffff
    Prefetchable memory behind bridge: 0000000081200000-00000000813fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    I/O behind bridge: 00007000-00007fff
    Memory behind bridge: 81400000-815fffff
    Prefetchable memory behind bridge: 0000000081600000-00000000817fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 18a0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f0704c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
    Memory behind bridge: f0400000-f04fffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1810 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 47
    I/O ports at 1c00 [size=8]
    I/O ports at 18d4 [size=4]
    I/O ports at 18d8 [size=8]
    I/O ports at 18d0 [size=4]
    I/O ports at 18e0 [size=32]
    Memory at f0704000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: medium devsel, IRQ 5
    Memory at 81800000 (32-bit, non-prefetchable) [size=256]
    I/O ports at 1c20 [size=32]
    Kernel modules: i2c-i801

07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
    Subsystem: Toshiba America Info Systems Satellite P305D-S8995E
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at 81000000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at 6000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

08:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
    Subsystem: Askey Computer Corp. Device 7096
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at 81400000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k
    Kernel modules: ath5k

0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) (prog-if 10 [OHCI])
    Subsystem: Toshiba America Info Systems Satellite P305D-S8995E
    Flags: bus master, stepping, medium devsel, latency 32, IRQ 16
    Memory at f0400000 (32-bit, non-prefetchable) [size=4K]
    Memory at f0402000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02) (prog-if 01)
    Subsystem: Toshiba America Info Systems Satellite P305D-S8995E
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at f0402800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
    Subsystem: Toshiba America Info Systems Satellite P305D-S8995E
    Flags: slow devsel, IRQ 11
    Memory at f0401000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>




```


Also, it seems this guy had a similar problem as I did, but his problem was hardware related. 
[http://ubuntuforums.org/showthread.php?t=1126372](http://ubuntuforums.org/showthread.php?t=1126372)

I hope it is not a hardware problem, because the computer that I am trying this on is a laptop and gutting one of those is... yeah.... very hard.
-DeathbyLinux

---

### Post by DeathByLinux on 2011-10-15
Just bouncing ideas here: if I have the driver as you say,  could I try uninstalling it and reinstalling it? Thoughts?
-DeathbyLinux

---

### Post by wildmanne39 on 2011-10-15
Hi, that is what was trying to do with the commands in the previous post reinstall the driver and firmware that would most likely fix your problem, but I do not know how to do it without an internet connection.
Thank you

---

### Post by wildmanne39 on 2011-10-15
Hi, please try:
```
sudo modprobe ath5k
```
```
sudo ifup wlan0
```
Thank you

---

### Post by DeathByLinux on 2011-10-16
nav@nav-Satellite-U400:~$ sudo modprobe ath5k
[sudo] password for nav: 
nav@nav-Satellite-U400:~$ sudo modprobe ath5k
nav@nav-Satellite-U400:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
nav@nav-Satellite-U400:~$

---

### Post by wildmanne39 on 2011-10-16
Hi So I guess your wireless did not come on after you loaded ath5k?

I looked for a way to install the driver and firmware from a usb drive, I thought I found the answer but one step required an internet connection.
Thank you

---

### Post by DeathByLinux on 2011-10-22
So, I think this is a hardware issue and so I went out and bought a wireless adapter, but I need to install it and it is a windows application. :( FML

---

### Post by wildmanne39 on 2011-10-23
Hi, if you mean it is a usb adapter please post the results of:
```
lsusb
```
with the adapter plugged in.
Thank you

---

### Post by DeathByLinux on 2011-10-26
```
 lsusbnav@nav-Satellite-U400:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 05dc:a810 Lexar Media, Inc. 
Bus 001 Device 007: ID 2001:3308 D-Link Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
nav@nav-Satellite-U400:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 009: ID 05dc:a810 Lexar Media, Inc. 
Bus 001 Device 007: ID 2001:3308 D-Link Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
I am going to attempt something and let me know what you think of my plan.

I have  a live USB with 11.10 on it. Now, I have allotted some space on there and I am going to do the following:
1. Put the USB in a computer that has working wifi/wired.
2. Install WINE and then install the driver for the USB internet adapter on the USB, so my live USB will know how to run the device, even if my computer hard drive does not.
I am just speaking from logic here and I am assuming that IF the live USB has the driver on it, I should be able to simply plug in the live USB and the adapter should work.

Does this plan make any sense?

-DeathbyLinux

---

### Post by wildmanne39 on 2011-10-27
Hi, wine is not used for what you want to use it for.

I tried to look up your usb adapter it does not have any linux drivers for it from what I could tell, you will need to use ndiswrapper and a windows xp driver for it, here is a link to get help with that, I do not know much about using ndiswrapper and at this link is all that they do.
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)
I hope they can help.
Good Luck

---

### Post by DeathByLinux on 2011-10-27
Is there a brand of usb adapter that Linux does support? I can still return the thing and buy another one if it is a better fit.

---

### Post by wildmanne39 on 2011-10-27
Hi, that is real hard to say some people claim one model and brand works out of the box with ubuntu and other people claim it did not work at all.

Even if a certain brand is known to work if you get a brand new version of that same brand it may not be supported yet without ndiswrapper because it takes time for linux drivers to catch up with new hardware.

Here is a link for cards and usb adapters that work and with what method, but some of it may be out dated.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Plus you are still going to need away to install with out internet connection. 
Thank you

---

### Post by DeathByLinux on 2011-11-02
Sorry Wildman, that article only lays out wireless cards and not adapters. :( Am I missing something?
-DeathbyLinux

---

### Post by wildmanne39 on 2011-11-02
Hi, that page shows usb devices and internal devices.
You will just have to click on each link and look because there is so much information there.
Thank you

---

### Post by DeathByLinux on 2011-11-12
Okay, 
      this is really embarrassing, but let me start by saying that I have fixed the problem. I guess this could happen to the best of us but let me try and salvage myself, here. Let me give you guys a brief history, but you don't have to read.
      I installed 11.04 about a month and a half ago and all was working well and then in the middle of the night that I installed it, the internet stopped working. I was puzzled, but decided to leave the problem for further investigation in the morning. Then, I started this very lengthy process of trying to figure out what was wrong and tried various "out of the box" ideas like the one about installing a USB internet adapter and even trying to install it on a USB live stick. 
       I had pretty much given up hope and planned to take the computer (a laptop) apart in the coming months and try and figure out the problem. Yesterday, due to high winds, the power kept turning off and on. The computer in question is very badly damaged physically, but the internal components are good. This means that the keyboard, mouse, display, battery and the AC adapter on this laptop are not working well and I use it by attaching external keyboard, mouse and display and have to keep the wire on the adapter in a way so that it does not cut supply to the computer and turn off the computer in a damaging manner.          
       For some reason, due to the power outage, the adapter started acting funny and the computer would not even turn on. I started to investigate and trying to reposition the adapter so there would be a steady supply of current to the computer and I discovered something that blew me away. Supposedly, aside from the function wifi (FN + F8 for turning wifi on and off), there exists a switch for turning the internet on and off. This button is located in the area around where the laptop's mouse pad is. 
       Once I made the adapter work and turned on the computer, my computer was able to detect the wireless networks in the area and I am sitting here typing on the Linux computer. 
       Concluding Notes
1) Never laugh at the "is it plugged in" question. It happens to the best of us that we miss a very minor detail which can lead to us searching for answers in all the wrong places. I would suggest that if a newbie reports these kinds of problems in the future, ask them if they have disabled whatever the issue is on the physical computer itself. There are a plethora of things on these laptops that are enabled and disabled using the Function (FN) key. 

2) There is still a mystery that I might want to research and that is the fact that disabling the wifi using this button also disabled the wired connection as well. I don't know if this button disables all forms of internet or just the wirelss. When I look at it, it has the symbol of wifi, which is the antenna with sine waves going outward. I am going to ask Toshiba about this and find out why disabling this disables the wired connection as well.

3) I want to thank all of you guys for trying your best to help me out. I would like to thank Wildeman most of all for his relentless efforts on this issue. He has helped me out in other issues before and deserves recognition for his endless efforts. 

-Forever grateful, DeathbyLinux

---

### Post by wildmanne39 on 2011-11-12
Hi, your welcome! I am glad you have it working.

The reason I did not mention the switch is according to this command:
```
rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
the switch was not off, I have never heard of wireless being turned off by a switch and a fn key both, that is indeed a strange situation.
Enjoy

---

