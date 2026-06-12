---
title: "No wireless ubuntu 11.04 on Dell XPS m1530"
date: 2011-05-30
forum: General Help
---

### Post by searayman on 2011-05-30
My dell xps m1530, has just been upgraded to 11.04 with a clean install and I can not get my wireless drivers to work. I just can not connect...

Any ideas would be greatly appreciated!

---

### Post by searayman on 2011-05-30
bump....please help I would like to be able to use my laptop again....

---

### Post by linuxinstalledfromhdd on 2011-05-30
Did your wireless drivers work in a previous version of Ubuntu? Say 10.10?

---

### Post by drpjkurian on 2011-05-30
Hi
Please give the output of
```
lspci
``` to find out the wireless card.

---

### Post by searayman on 2011-05-31
> **drpjkurian said:**
> Hi
Please give the output of
```
lspci
``` to find out the wireless card.

The wireless card is:

Broadcom Corporation BCM4321 82.11a/g/n (rev 03)

---

### Post by searayman on 2011-05-31
anybody else?

---

### Post by garvinrick4 on 2011-05-31
Install these two in Synaptics: Check additional drivers to enable:
Have to reboot after installing:

---

### Post by searayman on 2011-05-31
> **garvinrick4 said:**
> Install these two in Synaptics: Check additional drivers to enable:
Have to reboot after installing:

OK, thanks trying this now. Will let you know if this works

---

### Post by samguerra on 2011-06-23
I installed the Synaptic Package Manager, and installed the two drivers. IT WORKS!!!!

---

### Post by shogun771 on 2011-07-08
Hey I have the same model machine and same problem. Ubuntu was working great till i updated to 11.04   

I installed the 2 things you screenshot 

bcmwl-kernel-source 

b43-fwcutter 

how should i proceed next>? hopefully this will solve my problem as well. Thanks.

---

### Post by wildmanne39 on 2011-07-09
> **shogun771 said:**
> Hey I have the same model machine and same problem. Ubuntu was working great till i updated to 11.04   

I installed the 2 things you screenshot 

bcmwl-kernel-source 

b43-fwcutter 

how should i proceed next>? hopefully this will solve my problem as well. Thanks.
HI, do you have the exact same card as the poster who fixed his issues? If not then this method probably will not work, if you do not know, run these commands in a terminal, you should run them anyway it will make it easier to help you.
```
sudo lshw -C network
```
```
lspci -nn
```
```
iwconfig
```
```
lsmod
```
 and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by shogun771 on 2011-07-16
sorry for my untimely response, thanks. 



**for sudo lshw -C network**

```
SCSI                      
  *-network        
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:15:c5:86:43:3a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=10.10.10.9 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f9ffc000-f9ffffff ioport:de00(size=256)
  *-network UNCLAIMED
       description: Network controller
       product: BCM4311 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f9efc000-f9efffff

``` 


**for lspci -nn** 

```
Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G86 [GeForce 8400M GS] [10de:0427] (rev a1)
03:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

``` 


**for iwconfig ** 

```
 lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.
 
```


[B]
for lsmod [/B]

```
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
vesafb                 13761  1 
binfmt_misc            17565  1 
vboxnetadp             13340  0 
vboxnetflt             28297  0 
vboxdrv               252684  2 vboxnetadp,vboxnetflt
nvidia              10709116  42 
snd_hda_codec_idt      71137  1 
snd_hda_intel          33211  1 
snd_hda_codec         103804  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
wl                   2568244  0 
joydev                 17606  0 
uvcvideo               72195  0 
dell_wmi               12681  0 
videodev               82052  1 uvcvideo
sparse_keymap          13898  1 dell_wmi
snd_timer              29602  2 snd_pcm,snd_seq
dell_laptop            13827  0 
v4l2_compat_ioctl32    17078  1 videodev
dcdbas                 14438  1 dell_laptop
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
r852                   18246  0 
sm_common              16817  1 r852
snd                    67382  11 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19438  0 
psmouse                73535  0 
nand                   55112  2 r852,sm_common
nand_ids               12723  1 nand
nand_ecc               13230  1 nand
mtd                    27900  2 sm_common,nand
serio_raw              13166  0 
lib80211               14991  1 wl
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
firewire_ohci          40370  0 
sdhci_pci              13989  0 
ahci                   25951  2 
sdhci                  27387  1 sdhci_pci
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
libahci                26642  1 ahci
sky2                   58509  0  
```

---

### Post by shogun771 on 2011-07-19
I'm sorry I replied a few days late but could anyone still give me a hand? It'd be greatly appreciated.

---

### Post by shogun771 on 2011-07-20
*

---

### Post by rbuck01 on 2012-06-28
> **shogun771 said:**
> I'm sorry I replied a few days late but could anyone still give me a hand? It'd be greatly appreciated.
I'm running Xubuntu on my XPS M1530, and I am not particularly tech savvy, but in case anyone else reads this thread looking for an answer, I got my solution from this website:
[http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/](http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/)

Uninstall bcmwl-kernel-source.
Install firmware-b43-installer.
Reboot.

Hope that helps.

---

