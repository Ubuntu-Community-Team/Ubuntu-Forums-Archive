---
title: "Wireless network problem (and partial solution)"
date: 2011-08-03
forum: General Help
---

### Post by DanR01 on 2011-08-03
Although I get the message 'connected to network' at startup I am unable to access any web pages.

Using the command ```
sudo ifconfig wlan0 down
``` and then ```
sudo ifconfig wlan0 up
``` allows me to connect.

Is there a way to run these two commands as a bash script on startup to avoid me having to enter them manually and could anyone point me in the right direction?

Thanks
Dan

---

### Post by wildmanne39 on 2011-08-03
Hi, I am going to be out of town tomorrow for a while but run these commands and post the outcome here and if someone does not help you before I get back I will give it my best shot then.
```
sudo lshw -C network 
```
```
nm-tool
```
```
lspci -nn | grep 0280
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
Thank you

---

### Post by edwardhigh on 2011-08-04
Thanks for Sharing .

[Online Diploma](http://www.edwardhighschool.com/)

---

### Post by marshag63 on 2011-08-04
Right click on the networking icon in the system tray and it will show you options and look at "connection information."  Also, make sure Enable networking and Enable wireless have check marks next to them.

You can also "edit connection" from there - make sure your settings are right.  Click the wireless tab, click on your network name, choose "Edit" and make sure "connect automaticaly" has a check mark in the box.

Hope this helps.

MDG

---

### Post by DanR01 on 2011-08-04
Thanks for the replies everyone. Connect automatically is set as is enable wireless networking.

There is quite a lot of output from the commands. From top to bottom:
 
```
 
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 82577LC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: 00:26:b9:63:96:fe
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 firmware=0.10-6 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:f0f00000-f0f1ffff memory:f0f24000-f0f24fff ioport:1800(size=32)
  *-network
       description: Wireless interface
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:63:d9:a4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-10-generic-pae firmware=8.83.5.1 build 33692 ip=192.168.0.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:f0a00000-f0a01fff
```
```
NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        00:26:B9:63:96:FE

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto SKY217AE] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             connected
  Default:           yes
  HW Address:        00:21:6A:63:D9:A4

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    LenWireless:     Infra, 00:1D:92:17:11:2D, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WEP
    BTHomeHub2-6KPN: Infra, 00:24:2C:13:D8:1B, Freq 2442 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    BTFON:           Infra, 02:24:2C:13:D8:1D, Freq 2442 MHz, Rate 54 Mb/s, Strength 31
    BTHomeHub2-N3NT: Infra, 00:21:04:81:DC:EA, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    BTHomeHub2-W72F: Infra, 00:24:2B:47:D2:48, Freq 2442 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    BTFON:           Infra, 12:FE:F4:4E:0D:28, Freq 2437 MHz, Rate 54 Mb/s, Strength 35
    O2wireless456999:Infra, 00:1D:68:F0:E8:5F, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WEP
    SKY08836:        Infra, 00:18:4D:F4:97:0C, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA
    SKY20118:        Infra, C0:D0:44:3D:4E:97, Freq 2412 MHz, Rate 54 Mb/s, Strength 38 WPA
    *SKY217AE:       Infra, C8:CD:72:C2:17:AF, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    SKY65817:        Infra, 5C:D9:98:BF:1D:9B, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    BTFON:           Infra, 0A:21:04:C5:4C:EA, Freq 2437 MHz, Rate 54 Mb/s, Strength 41
    BTOpenzone:      Infra, 02:24:17:A7:4E:EE, Freq 2457 MHz, Rate 54 Mb/s, Strength 32
    BTFON:           Infra, 02:24:17:A7:4E:EF, Freq 2457 MHz, Rate 54 Mb/s, Strength 34
    BTOpenzone:      Infra, 06:8B:5D:B7:DF:32, Freq 2462 MHz, Rate 54 Mb/s, Strength 54
    BTOpenzone:      Infra, 06:21:04:C5:4C:EA, Freq 2437 MHz, Rate 54 Mb/s, Strength 40
    BTFON:           Infra, 0A:8B:5D:B7:DF:32, Freq 2462 MHz, Rate 54 Mb/s, Strength 55
    BTHomeHub2-M44F: Infra, 00:24:17:A7:4E:ED, Freq 2457 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    BTHomeHub2-N4QH: Infra, 00:21:04:C5:4C:EA, Freq 2437 MHz, Rate 54 Mb/s, Strength 38 WPA WPA2
    BTHomeHub2-C3NG: Infra, 00:8B:5D:B7:DF:32, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1
``````
07:00.0 Network controller [0280]: Intel Corporation Ultimate N WiFi Link 5300 [8086:4235]
``````
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"SKY217AE"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C8:CD:72:C2:17:AF   
          Bit Rate=72.2 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1129  Invalid misc:14   Missed beacon:0
``````
rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
``````
lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
rfcomm                 38125  12 
sco                    17827  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
btusb                  18160  2 
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  308 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  1 
vesafb                 13449  1 
snd_hda_codec_idt      60537  1 
nvidia              10390877  44 
arc4                   12473  2 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
iwlagn                284778  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
iwlcore               148965  1 iwlagn
snd_seq_midi_event     14475  1 snd_seq_midi
uvcvideo               66851  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
mac80211              257001  2 iwlagn,iwlcore
r852                   17878  0 
sm_common              16737  1 r852
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
nand                   49822  2 r852,sm_common
videodev               75143  1 uvcvideo
psmouse                59039  0 
joydev                 17322  0 
nand_ids                8547  1 nand
nand_ecc               13070  1 nand
i7core_edac            23249  0 
serio_raw              12990  0 
mtd                    26530  2 sm_common,nand
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              156212  3 iwlagn,iwlcore,mac80211
edac_core              42881  3 i7core_edac
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
sdhci_pci              13623  0 
ahci                   21591  2 
firewire_ohci          31504  0 
sdhci                  22720  1 sdhci_pci
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
libahci                25548  1 ahci
e1000e                138627  0 
video                  18951  0 



```

---

### Post by cdoebbler on 2011-08-04
I have a similar problem with a broadcom 4312 modem. I posted the below info sometime ago and people replied, but nothing worked. 

But I found an answer at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Here's feedback from same diagnoses.

> 

$ sudo lshw -C network


  *-network DISABLED      

       description: Wireless interface

       product: BCM4312 802.11b/g LP-PHY

       vendor: Broadcom Corporation

       physical id: 0

       bus info: pci@0000:01:00.0

       logical name: eth1

       version: 01

       serial: 0c:60:76:5e:40:18

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless

       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg

       resources: irq:16 memory:feafc000-feafffff

  *-network

       description: Ethernet interface

       product: AR8132 Fast Ethernet

       vendor: Atheros Communications

       physical id: 0

       bus info: pci@0000:02:00.0

       logical name: eth0

       version: c0

       serial: 00:26:55:cd:7f:75

       size: 100Mbit/s

       capacity: 100Mbit/s

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.37 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s

       resources: irq:44 memory:febc0000-febfffff ioport:ec80(size=128)

$ nm-tool



NetworkManager Tool



State: connected



- Device: eth1 -----------------------------------------------------------------

  Type:              802.11 WiFi

  Driver:            wl

  State:             unavailable

  Default:           no

  HW Address:        0C:60:76:5E:40:18



  Capabilities:



  Wireless Properties

    WEP Encryption:  yes

    WPA Encryption:  yes

    WPA2 Encryption: yes



  Wireless Access Points 





- Device: eth0  [Auto eth0] ----------------------------------------------------

  Type:              Wired

  Driver:            atl1c

  State:             connected

  Default:           yes

  HW Address:        00:26:55:CD:7F:75



  Capabilities:

    Carrier Detect:  yes

    Speed:           100 Mb/s



  Wired Properties

    Carrier:         on



  IPv4 Settings:

    Address:         192.168.1.37

    Prefix:          24 (255.255.255.0)

    Gateway:         192.168.1.1



    DNS:             194.230.1.103

    DNS:             194.230.1.71



$ lspci -nn | grep 0280

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)


$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



eth1      IEEE 802.11  Access Point: Not-Associated   

          Link Quality:5  Signal level:0  Noise level:0

          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

$ rfkill list all

0: hci0: Bluetooth

	Soft blocked: no

	Hard blocked: no

1: brcmwl-0: Wireless LAN

	Soft blocked: no

	Hard blocked: yes

2: hp-wifi: Wireless LAN

	Soft blocked: no

	Hard blocked: no


$ lsmod

Module                  Size  Used by

binfmt_misc            13213  1 

parport_pc             32111  0 

ppdev                  12849  0 

rfcomm                 38125  8 

snd_hda_codec_idt      60537  1 

snd_hda_intel          24140  2 

snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel

sco                    17827  2 

snd_hwdep              13274  1 snd_hda_codec

snd_pcm                80042  2 snd_hda_intel,snd_hda_codec

bnep                   17785  2 

snd_seq_midi           13132  0 

joydev                 17322  0 

snd_rawmidi            25269  1 snd_seq_midi

l2cap                  48656  16 rfcomm,bnep

i915                  450934  3 

lib80211_crypt_tkip    17203  0 

snd_seq_midi_event     14475  1 snd_seq_midi

wl                   2642531  0 

drm_kms_helper         40745  1 i915

drm                   180037  4 i915,drm_kms_helper

snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event

snd_timer              28659  2 snd_pcm,snd_seq

snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq

btusb                  18160  2 

lp                     13349  0 

parport                36746  3 parport_pc,ppdev,lp

hp_wmi                 13418  0 

i2c_algo_bit           13184  1 i915

psmouse                73312  0 

uvcvideo               66851  0 

video                  18951  1 i915

sparse_keymap          13666  1 hp_wmi

snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

lib80211               14570  2 lib80211_crypt_tkip,wl

videodev               75143  1 uvcvideo

serio_raw              12990  0 

bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb

soundcore              12600  1 snd

snd_page_alloc         14073  2 snd_hda_intel,snd_pcm

ahci                   21591  2 

libahci                25548  1 ahci

atl1c                  36237  0 


---

### Post by wildmanne39 on 2011-08-04
Hi, @DanR01 I may have found the solution.

This problem is a known issue with the iwlagn driver, and the best workaround is to disable 802.11n on the card.

To disable 802.11n on this card create /edit your /etc/modprobe.d/options.conf file like this.
```
gksu gedit /etc/modprobe.d/options.conf 
```
And add the following to it.
> options iwlagn 11n_disable=1 11n_disable50=1
then save and exit.
Thank you

---

### Post by wildmanne39 on 2011-08-04
Hi, @cdoebbler
So are you having a problem with your wireless not connecting?

It says that you are hard blocked which usually means you need to turn your switch on, it may have a button to push or f11 or fn11 key something like that to turn it on..
Thank you

---

### Post by DanR01 on 2011-08-05
wildmanne39, your solution worked. 

Thank you.

---

### Post by wildmanne39 on 2011-08-05
Hi, your welcome!I am glad it worked, enjoy your wireless.

---

