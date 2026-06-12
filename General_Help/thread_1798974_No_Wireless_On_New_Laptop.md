---
title: "No Wireless On New Laptop"
date: 2011-07-06
forum: General Help
---

### Post by LonelyAspie on 2011-07-06
I bought a new laptop a few hours ago and notice that the wireless doesn't work on it, however, the Ethernet and everything else does.

I am using a Toshiba Satellite L775-00P with Linux: Ubuntu 10.10.

---

### Post by gizmo720 on 2011-07-06
Do you know the model of your wireless card?

---

### Post by wildmanne39 on 2011-07-07
> **LonelyAspie said:**
> I bought a new laptop a few hours ago and notice that the wireless doesn't work on it, however, the Ethernet and everything else does.

I am using a Toshiba Satellite L775-00P with Linux: Ubuntu 10.10.Hi, put these commands in a terminal 
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

### Post by seawolf167 on 2011-07-07
Do you have any wireless drivers available under "Additional Drivers", which can be accessed by clicking the power button in the upper right, selecting "System Settings", then "Additional Drivers". Note that you need to be connected to the internet via your ethernet cable for it to search for and download possible drivers for you to activate.

---

### Post by LonelyAspie on 2011-07-07
> **seawolf167 said:**
> Do you have any wireless drivers available under "Additional Drivers", which can be accessed by clicking the power button in the upper right, selecting "System Settings", then "Additional Drivers". Note that you need to be connected to the internet via your ethernet cable for it to search for and download possible drivers for you to activate.

I already tried that and nothing comes up.

From SysInfo
> **Network Controller:**
Realtek Semiconductor Co., Ltd. Device 8176 (rev01)
Subsystem: Realtek Semiconductor., Ltd. Device 8182
**Ethernal Controller**
Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet Controller (rev 05)
Subsystem: Toshiba America Info System Device fc66Here's the link tot the laptop I bought, not sure if there is anything there that will help:
[http://www.staples.ca/ENG/Catalog/cat_sku.asp?CatIds=&webid=330194&affixedcode=WW](http://www.staples.ca/ENG/Catalog/cat_sku.asp?CatIds=&webid=330194&affixedcode=WW)

> **wildmanne39 said:**
> Hi, put these commands in a terminal 
```
sudo lshw -C network 
``````
lspci -nn
``````
iwconfig

``````
lsmod
```and post the outcome  here by clicking on new  reply and click # and paste the information between the  brackets.

**Aspie@Toshiba-Satellite-L775:~$ sudo lshw -C network**
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:c000(size=256) memory:f6a00000-f6a03fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 05
       serial: e0:69:95:98:c9:9f
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.100 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:46 ioport:a000(size=256) memory:f0b04000-f0b04fff memory:f0b00000-f0b03fff


**Aspie@Toshiba-Satellite-L775:~$ lspci -nn **
00:00.0 Host bridge [0600]: Intel Corporation Sandy Bridge DRAM Controller [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Sandy Bridge Integrated Graphics Controller [8086:0116] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.1 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 2 [8086:1c12] (rev b5)
00:1c.3 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 4 [8086:1c16] (rev b5)
00:1c.5 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 6 [8086:1c1a] (rev b5)
00:1c.6 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 7 [8086:1c1c] (rev b5)
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation Cougar Point LPC Controller [8086:1c49] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation Cougar Point 6 port SATA AHCI Controller [8086:1c03] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 05)
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
03:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev  05)

**Aspie@Toshiba-Satellite-L775:~$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

**Aspie@Toshiba-Satellite-L775:~$ lsmod**
Module                  Size  Used by
parport_pc             26378  0 
ppdev                   5556  0 
snd_hda_codec_intelhdmi     9812  1 
snd_hda_codec_realtek   218460  1 
binfmt_misc             6599  1 
joydev                  8767  0 
snd_hda_intel          22299  2 
snd_hda_codec          87552  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71603  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
i915                  296491  3 
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
drm_kms_helper         30200  1 i915
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168796  3 i915,drm_kms_helper
uvcvideo               55943  0 
snd                    49102  13  snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59033  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
serio_raw               4022  0 
intel_agp              26926  2 i915
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
agpgart                32107  2 drm,intel_agp
xhci_hcd               55197  0 
soundcore                880  1 snd
output                  1883  1 video
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40524  1 
r8169                  36841  0 
ahci                   19326  2 
libahci                21792  1 ahci
mii                     4425  1 r8169

---

### Post by wildmanne39 on 2011-07-07
HI, is your wireless usb? if so run this command also.
```
lsusb
```

---

### Post by LonelyAspie on 2011-07-07
> **wildmanne39 said:**
> HI, is your wireless usb? if so run this command also.
```
lsusb
```

No, I'm using the internal wireless card. I don't think I have a USB wireless with me.

---

### Post by wildmanne39 on 2011-07-07
> **LonelyAspie said:**
> No, I'm using the internal wireless card. I don't think I have a USB wireless with me.
Hi, do you have a button that turns it on or off, some laptops and net books you have to use a fn key.

---

### Post by LonelyAspie on 2011-07-07
> **wildmanne39 said:**
> Hi, do you have a button that turns it on or off, some laptops and net books you have to use a fn key.

Yes, I've checked it last night. WHen I click on it, there is no spot for the wireless, it just says (Wired Connection: Disconnected). I'm on my Mom's computer right now which runs the same OS.

---

### Post by wildmanne39 on 2011-07-07
> **LonelyAspie said:**
> Yes, I've checked it last night. WHen I click on it, there is no spot for the wireless, it just says (Wired Connection: Disconnected). I'm on my Mom's computer right now which runs the same OS.Hi, I meant that wireless on laptops sometimes have a button on the laptop itself that can be turned on or off, also you might look at the documentation that came with your computer some have wireless that is turned on and off by hitting certain keys on the key board like fn key. The reason I ask is that in the information that you post that I asked for I do not see a wireless card.

---

### Post by LonelyAspie on 2011-07-07
> **wildmanne39 said:**
> Hi, I meant that wireless on laptops sometimes have a button on the laptop itself that can be turned on or off, also you might look at the documentation that came with your computer some have wireless that is turned on and off by hitting certain keys on the key board like fn key. The reason I ask is that in the information that you post that I asked for I do not see a wireless card.

It can be disabled by hitting FN+F8. I tried enabling and and disabling it a couple times.

---

### Post by wildmanne39 on 2011-07-07
> **LonelyAspie said:**
> It can be disabled by hitting FN+F8. I tried enabling and and disabling it a couple times.
Hi, try this and post the out put.
```
sudo lspci
```

---

### Post by LonelyAspie on 2011-07-07
> **wildmanne39 said:**
> Hi, try this and post the out put.
```
sudo lspci
```

I'm on my Mom's computer now, but I can copy the text to a jump drive and switch it to this computer via USB and paste it here.

> 
**Aspie@Toshiba-Satellite-L775:~$ sudo lspci**
00:00.0 Host bridge: Intel Corporation Sandy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 6 (rev b5)
00:1c.6 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 7 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Cougar Point LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
03:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)


---

### Post by chili555 on 2011-07-07
> Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [[COLOR="Red"]10ec:8176[/COLOR]] (rev 01)Please check here: [http://ubuntuforums.org/showthread.php?t=1618554](http://ubuntuforums.org/showthread.php?t=1618554)

[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667)

Post back in about ten minutes and tell us if wireless is rockin'.

---

### Post by walt.smith1960 on 2011-07-07
delete

---

### Post by wildmanne39 on 2011-07-07
> **chili555 said:**
> Please check here: [http://ubuntuforums.org/showthread.php?t=1618554](http://ubuntuforums.org/showthread.php?t=1618554)

[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667)

Post back in about ten minutes and tell us if wireless is rockin'.
Hi, thanks chili I was just doing a search to see if I could find a link for his card when I say that you had posted so I came here to see if you had the answer, I appreciate the help.

---

### Post by LonelyAspie on 2011-07-07
Hi,

I tried this:

```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```

but it dosen't work. Terminal seemed to have a problem. 

**Aspie@Toshiba-Satellite-L775:~$** sudo add-apt-repository ppa:lexical/hwe-wireless
Error reading [http://launchpad.net/api/1.0/~hwe-wireless/+archive/ppa:]("http://launchpad.net/api/1.0/%7Ehwe-wireless/+archive/ppa:") <urlopem error [Errno -2] Name or service not known>

---

### Post by wildmanne39 on 2011-07-07
> **LonelyAspie said:**
> Hi,

I tried this:

```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```

but it dosen't work. Terminal seemed to have a problem. 

**Aspie@Toshiba-Satellite-L775:~$** sudo add-apt-repository ppa:lexical/hwe-wireless
Error reading [http://launchpad.net/api/1.0/~hwe-wireless/+archive/ppa:]("http://launchpad.net/api/1.0/%7Ehwe-wireless/+archive/ppa:") <urlopem error [Errno -2] Name or service not known>
Hi, on the page where you got that just above where it shows that ppa, follow those directions and get the driver from the realtek website.

---

### Post by wildmanne39 on 2011-07-08
Hi, I have look 3 times through there web site but I can not fine the driver for that card.

---

### Post by LonelyAspie on 2011-07-08
I downloaded the driver that mentioned on the page and it looked like it was installing, I restarted the computer and it did not work, unfortunately.

I worked until the last part where it said make file. Are you sure I have the same card model number as the one the other site?

I can't ev en find the Windows driver. The laptop is so new, the Toshiba doesn't even have it on their site yet :(

---

### Post by wildmanne39 on 2011-07-08
HI, I found the driver it is the RTL8192CE-VA4, this is the link to get the driver,
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2782](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2782)
just paste that driver number in the search box and it will find it for you. Then follow the directions on that other page on launch pad.

---

### Post by LonelyAspie on 2011-07-08
> **wildmanne39 said:**
> HI, I found the driver it is the RTL8192CE-VA4, this is the link to get the driver,
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2782](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2782)
just paste that driver number in the search box and it will find it for you. Then follow the directions on that other page on launch pad.


Thank you very much, it works! :) Just one thing, how do I get it so when I ever install Ubuntu on this laptop again, I don't have to install the driver again and how come it wasn't included with the list of drivers on the CD?

---

### Post by wildmanne39 on 2011-07-08
> **LonelyAspie said:**
> Thank you very much, it works! :) Just one thing, how do I get it so when I ever install Ubuntu on this laptop again, I don't have to install the driver again and how come it wasn't included with the list of drivers on the CD?Hi, if you reinstall you will have to do it again, unless it is included in the additional drivers in the next release. I do not know why it was not they try to include as many as  possible, it might just be the one they included did not work, that is a problem with some of the broadcom drivers,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by jtarin on 2011-07-08
He,he:p

---

