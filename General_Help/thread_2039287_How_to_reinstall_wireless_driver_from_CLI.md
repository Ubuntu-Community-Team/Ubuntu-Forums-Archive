---
title: "How to reinstall wireless driver from CLI?"
date: 2012-08-08
forum: General Help
---

### Post by TheHimself on 2012-08-08
I have a Lenovo laptop and my wireless is not working properly. Maybe reinstalling the driver can help. The jockey-gtk application says there are no proprietary drivers in use.

---

### Post by kurt18947 on 2012-08-08
Reinstalling may help, it may not.  I'd suggest posting what kind of wifi chipset you have and perhaps someone will have a suggestion.  Assuming this is an internal wifi adapter, if you could open a terminal, type "lspci", copy and paste the output that'd be a good start.  I believe some Thinkpads use Broadcom chipsets some of which do require post-install massaging.

---

### Post by TheHimself on 2012-08-09
Here it is:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
05:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
05:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
```

---

### Post by Bucky Ball on 2012-08-09
Odd. That should be working 'out of the box'. 

Please give the result of:

```
sudo lshw -C network
```

---

### Post by TheHimself on 2012-08-09
Here it is:

```

*-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1d:72:8e:d2:89
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 firmware=0.3-0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:fe000000-fe01ffff memory:fe025000-fe025fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1f:3c:6f:9e:60
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-32-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:45 memory:dfcff000-dfcfffff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: 76:79:72:77:f2:6a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.36 link=yes multicast=yes

```

---

### Post by kurt18947 on 2012-08-09
Odd indeed.  I have to resort of extraordinary measures to disable my Intel 3945ABG in order to use a faster adapter.  Perhaps try in a terminal "rfkill list".  If anything shows up as blocked, try "rfkill unblock all". (I think that's the proper syntax, please correct me if I'm wrong)

---

### Post by TheHimself on 2012-08-09
Nothing is blocked. Can it be a hardware problem? It *can* find the wireless networks but it can't connect to them. The wifi LED is on but it doesn't blink.

---

### Post by kurt18947 on 2012-08-09
> **TheHimself said:**
> Nothing is blocked. Can it be a hardware problem? It *can* find the wireless networks but it can't connect to them. The wifi LED is on but it doesn't blink.

My experience has been that if the light is on but not blinking it's a driver problem.  You wouldn't have a live CD/DVD or USB, would you?  Maybe try that.  I'm pretty much stumped.

---

### Post by Bucky Ball on 2012-08-09
Are you running a static IP? Are you running through a router or other access point? Is this your home network (LAN) or work/school?

I would go to the Network icon and 'Edit Connections'. Go to wireless and make sure all is correct there. 

You could try deleting the Wifi entry there, rebooting and see what it picks up. You look to have the driver installed from the output you gave of that command.

---

### Post by wildmanne39 on 2012-08-10
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/netscript.sh && chmod +x netscript.sh && ./netscript.sh
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by TheHimself on 2012-08-10
```

*************** info trace ****************



**** uname -a ****


Linux rez-laptop 2.6.35-32-generic #67-Ubuntu SMP Mon Mar 5 19:39:49 UTC 2012 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"


**** lspci ****


00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03)
	Subsystem: Lenovo Device [17aa:20de]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
	Subsystem: Intel Corporation Device [8086:1010]
	Kernel driver in use: iwl3945


**** lsusb ****


Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 047: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


**** iwconfig ****


wlan0     IEEE 802.11abg  ESSID:"hpsetup"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


**** rfkill ****


0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
128: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


**** lsmod ****


Module                  Size  Used by
option                 16661  0 
usb_wwan               12201  1 option
usbserial              40364  2 option,usb_wwan
rndis_wlan             28282  0 
rndis_host              7580  1 rndis_wlan
cdc_ether               4920  1 rndis_host
usbnet                 20985  3 rndis_wlan,rndis_host,cdc_ether
mii                     5261  1 usbnet
mmc_block               9971  0 
nls_iso8859_1           4657  0 
nls_cp437               6375  0 
vfat                   10954  0 
fat                    56244  1 vfat
usb_storage            50788  0 
cdc_acm                18539  0 
cryptd                  8140  0 
aes_x86_64              7936  0 
aes_generic            27631  1 aes_x86_64
rfcomm                 40819  4 
sco                     9986  2 
bnep                   11985  2 
l2cap                  42336  16 rfcomm,bnep
btusb                  13025  2 
bluetooth              59245  9 rfcomm,sco,bnep,l2cap,btusb
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_analog    80317  1 
arc4                    1497  2 
iwl3945                97066  0 
snd_hda_intel          26147  3 
snd_hda_codec         100919  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
pcmcia                 40944  0 
i915                  335457  4 
iwlcore               146875  1 iwl3945
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
mac80211              267131  2 iwl3945,iwlcore
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
thinkpad_acpi          78535  1 
tpm_tis                10022  0 
drm_kms_helper         32836  1 i915
drm                   206230  4 i915,drm_kms_helper
tpm                    16051  1 tpm_tis
psmouse                62126  0 
nvram                   7990  1 thinkpad_acpi
tpm_bios                6426  1 tpm
yenta_socket           24279  0 
pcmcia_rsrc            10357  1 yenta_socket
snd                    64277  18 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,thinkpad_acpi
serio_raw               4910  0 
cfg80211              170581  4 rndis_wlan,iwl3945,iwlcore,mac80211
pcmcia_core            17677  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit            6208  1 i915
video                  22176  1 i915
soundcore               1240  1 snd
intel_agp              32334  2 i915
output                  2527  1 video
lp                     10201  0 
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
parport                37032  3 parport_pc,ppdev,lp
sdhci_pci               8147  0 
ahci                   22370  4 
firewire_ohci          24999  0 
firewire_core          54391  1 firewire_ohci
e1000e                151819  0 
libahci                26148  1 ahci
sdhci                  18432  1 sdhci_pci
led_class               3393  2 thinkpad_acpi,sdhci
crc_itu_t               1739  1 firewire_core


**** nm-tool ****



NetworkManager Tool

State: connecting

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto hpsetup] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    hpsetup:         Ad-Hoc, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 28
    FreeWifi:        Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 28
    orange:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 31
    Livebox-908A:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    orange:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
    Livebox-93a8:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 31 WPA WPA2
    Livebox-e5e1:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 31 WPA WPA2




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false


**** NetworkManager.conf ****




**** interfaces ****


auto lo
iface lo inet loopback
iface lo inet dhcp


**** iwlist ****




**** resolv ****


# Generated by NetworkManager


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[541442.044041] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541442.626493] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541443.793277] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541444.336730] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541444.791854] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541445.356290] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541445.791383] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541446.331857] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541446.542367] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541447.081518] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541447.540609] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541448.118188] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541448.542162] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541449.111618] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541450.792165] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541451.353611] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541451.790743] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541452.366184] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541453.043197] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541453.628632] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541454.291644] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541455.103972] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541455.542084] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541456.140537] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541456.294743] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541457.140061] rndis_host 5-1:6.0: RNDIS init failed, -110
[541457.140101] rndis_host: probe of 5-1:6.0 failed with error -110
[541457.141364] rndis_wlan 5-1:6.0: RNDIS init failed, -71
[541457.141427] rndis_wlan: probe of 5-1:6.0 failed with error -71
[541457.612527] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541458.040968] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541458.596428] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541459.050515] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541459.641931] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541460.791747] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541461.337206] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541463.041775] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541463.600957] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541464.042323] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541464.632757] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541465.041894] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541465.624309] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541466.542206] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541467.102658] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541468.291449] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541468.858891] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541469.042107] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541469.620567] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541470.300512] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541471.150887] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541471.542011] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541472.081729] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541472.792026] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541473.374770] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541473.542081] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541474.104774] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541474.292111] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541474.884817] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541475.792195] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541476.330627] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541477.042294] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541477.598993] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541477.790229] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541478.358022] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541478.791371] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541479.382075] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541479.791437] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541480.359903] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541480.791499] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541481.380202] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541481.801516] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541482.358264] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541482.791612] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541483.361071] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541484.040668] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541484.599399] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541485.541748] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541486.104457] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541487.791901] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541488.327585] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541488.541945] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541489.080688] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541489.794011] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541490.347810] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541490.793057] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541491.374792] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541492.042123] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541492.593858] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541493.292210] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541493.834408] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541496.291380] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541496.848109] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541497.291442] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541497.862318] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541498.040168] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541498.573200] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541498.791571] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541499.371249] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541501.541682] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541502.771455] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541503.041781] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541503.621502] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541503.791827] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541504.381670] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541505.043874] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541505.605614] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541505.791941] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541506.371406] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541506.541986] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541507.133387] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541508.292088] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541508.855797] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541509.292134] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541509.847856] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541510.791204] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541511.367948] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541512.042285] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541512.580002] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541513.541362] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541514.091098] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541514.290401] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541514.862774] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541515.041465] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541515.618186] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541516.291547] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541516.833258] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541517.041564] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541517.596302] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541519.040692] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541519.605436] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541520.291770] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541520.870523] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541521.051788] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541521.640637] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541522.041853] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541522.577583] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541523.291978] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541524.101689] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541524.542011] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541525.101732] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541525.791086] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541526.363824] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541526.792142] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541527.331839] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541528.042210] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541528.888954] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541529.541304] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541530.089017] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541584.791009] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541585.616158] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541586.041729] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541586.583691] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541586.792145] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541587.358846] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541587.791708] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541588.350733] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541588.791230] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541589.349249] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541595.792083] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541596.612400] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541599.291516] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541601.150396] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541601.541527] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541602.113940] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541640.542255] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541641.342605] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541899.541480] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541900.359839] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[541903.291702] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[541905.153228] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[542014.041708] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[542015.903493] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[542022.541236] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[542024.411482] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[542027.291648] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[542027.839093] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[542028.292218] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[542028.818687] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[542255.041199] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[542256.890046] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[542257.041337] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[542257.867077] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[542351.291680] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[542352.091716] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[542354.541876] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[542355.360284] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[542357.541014] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[542358.107766] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[542359.541725] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[542360.115164] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[542366.041830] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[542366.859396] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[542370.541859] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[542371.100343] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[542392.542032] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[542393.365762] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[542395.542198] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[542396.121909] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[542397.291302] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[542399.158090] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[542428.045188] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[542428.848955] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[542439.041529] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[542439.837637] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[542440.791503] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[542441.377492] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[542463.041464] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[542463.861185] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[547060.411926] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[547353.794475] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[549870.873422] iwl3945 0000:03:00.0: Card state received: HW:Kill SW:On
[549873.195805] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[551229.547244] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[551967.422136] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[551992.251626] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[552228.716553] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[554409.158457] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[554421.733513] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[554422.269952] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[554556.415333] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[554557.187161] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[554702.930930] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[554703.691011] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[554713.865888] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[554714.647058] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[554741.581778] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[554742.359534] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[554763.104566] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[554763.861537] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[554802.573351] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[554803.351179] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[554816.598391] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[554818.380848] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[554839.907022] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[554841.187783] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[554867.876308] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[554868.642035] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[554887.097240] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[554887.881868] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[554909.879872] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[554910.637060] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[554912.010116] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[554912.561653] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[554932.182777] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[554932.679933] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[554958.142404] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[554958.933620] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[554959.442170] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[554959.960091] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[554988.538771] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[554989.039222] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555016.536094] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555017.321224] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555018.006505] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555018.543272] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555029.887134] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555030.676014] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555033.375394] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555033.868284] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555036.605018] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555037.099253] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555039.334658] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555039.829317] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555041.324547] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555043.150130] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555046.577018] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555047.093268] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555060.117292] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555060.897967] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555067.186938] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555068.469452] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555070.326083] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555070.859327] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555073.954491] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555074.462292] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555093.275277] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555094.069413] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555096.982436] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555097.492698] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555098.680917] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555099.186997] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555103.408374] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555104.163450] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555107.186983] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555107.682233] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555112.645269] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555114.431217] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555115.421895] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555115.920217] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555119.315020] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555119.834198] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555124.288125] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555125.073659] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555128.399458] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555128.901339] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555129.489015] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555129.990572] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555138.071561] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555138.832691] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555145.091004] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555145.851309] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555148.470671] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555148.961042] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555152.598022] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555154.420142] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555164.505777] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555165.267283] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555165.325956] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555165.842294] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555168.774802] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555169.521582] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555173.634566] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555174.388578] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[555179.397082] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[555180.347094] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[558295.791497] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[558423.812152] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[558424.021878] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[558427.082006] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[558434.393290] iwl3945 0000:03:00.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100506)
[558441.491432] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[558482.547223] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558482.690906] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558483.201322] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558485.670072] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558486.192137] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558487.156465] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558487.688588] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558487.790149] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558488.330868] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558489.736326] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558490.260798] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558497.507494] iwl3945 0000:03:00.0: Card state received: HW:Kill SW:On
[558499.497945] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558501.311319] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558501.868686] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558502.387476] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558503.038646] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558503.500448] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558508.147111] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558508.662625] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558512.108078] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558512.630876] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558521.403284] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558523.230982] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558524.623477] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558525.122244] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558527.053989] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558527.575386] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558528.674051] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558529.161034] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558529.982599] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558530.517584] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558532.020870] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558532.533105] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558533.798755] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558534.318780] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558535.958580] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558536.469612] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558536.623880] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558537.155430] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558537.310273] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558537.780985] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558538.852656] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558539.360957] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558544.828440] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558546.640733] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558547.498485] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558548.047389] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558557.803471] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558559.086410] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558560.031668] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558560.550920] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558561.684574] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558562.197240] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558563.740238] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558564.270116] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558564.327452] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558564.838971] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558564.846095] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558565.339841] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558566.017455] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558566.544077] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558568.082737] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558569.914443] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558570.271372] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558571.450602] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558573.339127] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558573.829461] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558574.223576] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558574.763167] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558575.208767] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558575.710341] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[558579.226332] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[558581.493655] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[559796.794661] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[559797.633397] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[560219.044142] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[560219.583850] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[560228.544175] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[560229.347475] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[560231.291791] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[560231.892177] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[560235.794507] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[560236.594107] rndis_host 5-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1, RNDIS device, <MAC address removed>
[565278.321614] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[566046.544470] rndis_host 5-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.0-1, RNDIS device
[566061.374506] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[566061.592169] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[566064.052937] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[566069.443288] iwl3945 0000:03:00.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100506)
[566075.831473] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[566076.997170] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[566092.404654] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566340.684020] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566341.460411] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566434.633989] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566435.388804] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566448.020132] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566448.800397] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566451.768691] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566452.280425] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566459.638961] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566460.414579] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566503.518151] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566504.270849] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566511.449091] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566511.949427] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566524.710352] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566525.220074] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566529.647468] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566530.439137] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566531.694447] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566532.220890] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566533.054573] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566533.548887] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566544.406157] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566544.927906] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566558.914289] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566559.670352] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566563.296504] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566564.051397] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566588.933105] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566589.681292] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566602.424755] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566603.182153] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566634.225673] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566634.983947] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566652.471388] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566653.241217] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566667.801950] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566669.601229] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566676.428568] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566676.950612] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566737.753173] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566738.510774] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566779.837599] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566780.351099] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566794.531903] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566795.279889] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566809.844275] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566810.590863] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566845.139306] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566845.921167] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566857.069050] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566857.580792] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566877.717239] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566878.508876] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566899.025888] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566899.779768] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566913.978859] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566914.480534] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566915.169344] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566915.670232] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566922.430700] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566923.197239] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566932.767932] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566933.522939] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[566936.126804] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[566936.640322] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[567578.748576] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[567579.244411] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[567989.028801] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[567990.850758] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[568014.180466] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[568016.002001] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[568060.135527] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[568061.940522] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[568346.592070] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[568348.385331] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[568377.339599] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[568379.145950] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[568382.480152] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[568384.310614] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[568403.971426] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[568405.773241] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[568414.725037] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[568416.529942] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[568425.296930] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[568426.052942] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[568466.886112] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[568468.699963] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[568472.347633] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[568472.837380] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[568490.112749] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[568491.901252] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[568519.595735] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[568521.420109] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[568551.024752] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[568552.841497] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[568590.440166] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[568592.254989] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[568633.567128] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[568635.386805] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[568728.063026] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[568729.859295] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[568731.283955] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[568731.795499] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[568749.735537] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[568751.570524] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[568894.800565] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[568895.567607] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[568967.173520] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[568967.950337] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[568996.286546] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[568997.056909] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[569015.262122] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[569016.038729] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[569028.662107] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[569029.432096] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[569133.205090] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[569133.957970] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[569178.870818] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[569179.367725] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[569183.051616] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[569184.882495] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[569188.705013] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[569190.002362] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[569218.744535] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[569219.514072] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[569282.382890] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[569283.142364] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[569286.274533] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[569288.117024] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[569421.792115] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[569422.549871] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[569790.045943] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[569809.732397] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[569809.962095] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[569812.604614] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[569817.873289] iwl3945 0000:03:00.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100506)
[569824.122403] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[569825.752440] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[569847.676898] iwl3945 0000:03:00.0: failed to remove IBSS station <MAC address removed>
[569848.300042] wlan0: no IPv6 routers present
[569857.698766] iwl3945 0000:03:00.0: failed to remove IBSS station <MAC address removed>
[569863.474831] iwl3945 0000:03:00.0: Card state received: HW:Kill SW:On
[569863.474967] iwl3945 0000:03:00.0: Not sending command - RF KILL
[569863.474976] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[569863.474986] iwl3945 0000:03:00.0: Error setting new configuration (-5).
[569863.474996] iwl3945 0000:03:00.0: failed to remove IBSS station <MAC address removed>
[569906.705502] rndis_host 2-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, <MAC address removed>
[570541.217569] rndis_host 2-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1d.7-1, RNDIS device
[571229.613296] iwl3945 0000:03:00.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100506)
[571254.526851] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[571434.304077] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[571487.082973] iwl3945 0000:03:00.0: Card state received: HW:Kill SW:On
[571880.413987] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[572176.123299] iwl3945 0000:03:00.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100506)
[572921.984775] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[572938.260481] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[572939.560247] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[572959.879405] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[572960.660981] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[572975.143536] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[572976.933264] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573020.573207] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573022.387720] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573066.714986] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573067.496635] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573080.784162] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573081.551711] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573083.813633] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573084.307504] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573096.300290] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573097.062505] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573102.702884] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573103.492052] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573105.896286] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573106.410581] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573113.262949] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573114.062437] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573119.916965] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573120.709792] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573122.035051] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573122.551936] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573134.172398] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573134.960457] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573147.509551] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573148.289739] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573150.649167] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573151.150730] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573159.723889] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573160.483361] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573169.953161] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573170.481386] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573172.650784] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573173.439356] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573175.820839] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573176.338476] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573182.095805] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573182.853105] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573185.227805] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573185.721028] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573188.639214] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573189.141109] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573190.738672] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573191.239482] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573192.838439] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573193.330653] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573197.406914] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573198.150689] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573203.626609] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573204.380708] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573208.787608] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573209.569069] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573217.666910] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573218.420433] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573223.192834] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573223.975712] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573226.724730] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573227.250652] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573228.004156] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573228.543891] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573234.184892] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573234.941102] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573237.274895] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573237.797484] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573240.831157] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573241.327486] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573242.538776] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573243.055970] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573246.072023] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573246.571098] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573248.851945] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573249.370973] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573251.782086] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573252.309944] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573253.533789] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573255.361559] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573259.566506] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573260.089958] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573261.707728] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573263.532772] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573266.634820] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573267.155801] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573267.585020] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573268.123354] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573275.476949] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573276.262038] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573279.720557] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573280.227533] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573291.089768] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573291.842598] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573293.141697] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573294.444267] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[573297.522739] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[573298.488886] rndis_host 4-1:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.1-1, RNDIS device, <MAC address removed>
[580069.533591] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[580084.472441] iwl3945 0000:03:00.0: Card state received: HW:Kill SW:On
[582331.792058] rndis_host 4-1:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.1-1, RNDIS device
[582355.473293] iwl3945 0000:03:00.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100506)
[582380.684504] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[582499.296395] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[582501.091230] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[582518.639594] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[582519.421458] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[582701.737234] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[582703.549327] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[582703.817248] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[582704.318801] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[582718.537578] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[582719.301395] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[583337.210392] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[583337.973738] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[583361.120787] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[583361.901376] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[583378.009375] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[583379.301583] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[583380.487052] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[583380.973073] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[583396.396892] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[583398.220578] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[585041.091956] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[585053.081444] iwl3945 0000:03:00.0: Master Disable Timed Out, 100 usec
[585056.483301] iwl3945 0000:03:00.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100506)
[585073.931864] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[587250.508481] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[590280.275020] rndis_host 1-3:6.0: usb0: register 'rndis_host' at usb-0000:00:1a.7-3, RNDIS device, <MAC address removed>
[590501.214018] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[590565.205501] iwl3945 0000:03:00.0: failed to remove IBSS station <MAC address removed>
[590569.618323] rndis_host 1-3:6.0: usb0: unregister 'rndis_host' usb-0000:00:1a.7-3, RNDIS device
[590575.241917] iwl3945 0000:03:00.0: failed to remove IBSS station <MAC address removed>
[590575.620054] wlan0: no IPv6 routers present
[590585.271145] iwl3945 0000:03:00.0: failed to remove IBSS station <MAC address removed>


**************** done ********************



```

---

### Post by wildmanne39 on 2012-08-10
Hi, your wireless is setup as ad-hoc you need to go into network manager settings and set it to infrastructure and DHCP to automatic, please delete, remove and purge all those settings from network manager, it will do all the work for you no need to manually setup anything.

Then do:
```
sudo iwconfig wlan0 mode managed
```

Also rndis_wlan and usb_wwan are loaded, it looks like you have an usb adapter plugged in and ethernet as well you will need to disconnect both of them then reboot.

Since 10.10 is not supported I am afraid to reinstall the driver because once it is removed we may not be able to install it again and it does not look like that is the issue anyway.
Reboot
Thanks

---

### Post by TheHimself on 2012-08-17
I did what you said and restarted and it now works. In my experience the problem arises when I turn the wireless manually off and then on.

---

### Post by wildmanne39 on 2012-08-17
Hi, turning off the wireless can be a problem with some laptops, unless you have to I suggest you leave it on, when you have a wired connection it will override the wireless anyway.
Thanks

---

