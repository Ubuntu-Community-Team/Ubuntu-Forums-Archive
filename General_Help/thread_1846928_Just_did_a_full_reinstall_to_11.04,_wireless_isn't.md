---
title: "Just did a full reinstall to 11.04, wireless isn't working!"
date: 2011-09-19
forum: General Help
---

### Post by hardisty on 2011-09-19
I've been searching around and googling, so if it helps:

> hardisty@TARDIS:~$ sudo lspci -k
[sudo] password for hardisty: 
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 1693
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 1693
	Kernel driver in use: i915
	Kernel modules: i915
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Hewlett-Packard Company Device 1693
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 1693
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Hewlett-Packard Company Device 1693
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 1693
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 1693
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 1693
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 1693
	Kernel modules: i2c-i801
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
	Subsystem: Hewlett-Packard Company Device 1693
	Kernel driver in use: intel ips
	Kernel modules: intel_ips
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 1693
	Kernel driver in use: r8169
	Kernel modules: r8169
02:00.0 Network controller: Ralink corp. Device 539f
	Subsystem: Hewlett-Packard Company Device 1637
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
	Subsystem: Hewlett-Packard Company Device 1693
	Kernel driver in use: rts_pstor
	Kernel modules: rts_pstor
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
	Subsystem: Hewlett-Packard Company Device 1693
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
	Subsystem: Hewlett-Packard Company Device 1693
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
	Subsystem: Hewlett-Packard Company Device 1693
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
	Subsystem: Hewlett-Packard Company Device 1693
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
	Subsystem: Hewlett-Packard Company Device 1693
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
	Subsystem: Hewlett-Packard Company Device 1693


I don't think the wireless card is there? I'm very lost. Any help would be appreciated!

---

### Post by user sam on 2011-09-19
Eh, does anything show up when you do "ifconfig"?

---

### Post by hardisty on 2011-09-19
hardisty@TARDIS:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 78:e3:b5:59:b2:7c  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7ae3:b5ff:fe59:b27c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:269646 errors:0 dropped:0 overruns:0 frame:0
          TX packets:148006 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:400205836 (400.2 MB)  TX bytes:10798846 (10.7 MB)
          Interrupt:40 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

---

### Post by hardisty on 2011-09-19
Also, if it matters, the light on the wireless button of my keyboard is consistently red, as opposed to white. Pressing it will turn the bluetooth off and on though

---

### Post by wildmanne39 on 2011-09-19
Hi, welcome to the forum! please run these commands and post the results here.
```
sudo lshw -C network
```
```
lspci -nn | grep -e 0280 -e 0200
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

### Post by hardisty on 2011-09-19
whoops, posted early. one second.

---

### Post by hardisty on 2011-09-19
here it is

> hardisty@TARDIS:~$ sudo lshw -C network
[sudo] password for hardisty: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 78:e3:b5:59:b2:7c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.108 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:3000(size=256) memory:b0404000-b0404fff memory:b0400000-b0403fff
  *-network UNCLAIMED
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:b4400000-b440ffff
hardisty@TARDIS:~$ lspci -nn | grep -e 0280 -e 0200
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
02:00.0 Network controller [0280]: Ralink corp. Device [1814:539f]
hardisty@TARDIS:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

hardisty@TARDIS:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
hardisty@TARDIS:~$ lsmod
Module                  Size  Used by
rfcomm                 38125  8 
binfmt_misc            13213  1 
sco                    17827  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_idt      60537  1 
snd_hda_intel          28209  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
i915                  451068  8 
snd_seq_midi           13132  0 
hp_wmi                 13418  0 
snd_rawmidi            25269  1 snd_seq_midi
sparse_keymap          13666  1 hp_wmi
snd_seq_midi_event     14475  1 snd_seq_midi
btusb                  18160  2 
drm_kms_helper         40745  1 i915
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               66851  0 
intel_ips              17769  0 
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
snd_timer              28659  2 snd_pcm,snd_seq
videodev               75143  1 uvcvideo
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   184164  4 i915,drm_kms_helper
psmouse                59039  0 
rts_pstor             348243  0 
serio_raw              12990  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
ahci                   21591  3 
libahci                25548  1 ahci
r8169                  46630  0 


---

### Post by hardisty on 2011-09-19
Sorry, put it quote by accident, if that matters.

```
hardisty@TARDIS:~$ sudo lshw -C network
[sudo] password for hardisty: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 78:e3:b5:59:b2:7c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.108 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:3000(size=256) memory:b0404000-b0404fff memory:b0400000-b0403fff
  *-network UNCLAIMED
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:b4400000-b440ffff
hardisty@TARDIS:~$ lspci -nn | grep -e 0280 -e 0200
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
02:00.0 Network controller [0280]: Ralink corp. Device [1814:539f]
hardisty@TARDIS:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

hardisty@TARDIS:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
hardisty@TARDIS:~$ lsmod
Module                  Size  Used by
rfcomm                 38125  8 
binfmt_misc            13213  1 
sco                    17827  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_idt      60537  1 
snd_hda_intel          28209  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
i915                  451068  8 
snd_seq_midi           13132  0 
hp_wmi                 13418  0 
snd_rawmidi            25269  1 snd_seq_midi
sparse_keymap          13666  1 hp_wmi
snd_seq_midi_event     14475  1 snd_seq_midi
btusb                  18160  2 
drm_kms_helper         40745  1 i915
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               66851  0 
intel_ips              17769  0 
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
snd_timer              28659  2 snd_pcm,snd_seq
videodev               75143  1 uvcvideo
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   184164  4 i915,drm_kms_helper
psmouse                59039  0 
rts_pstor             348243  0 
serio_raw              12990  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
ahci                   21591  3 
libahci                25548  1 ahci
r8169                  46630  0 

```

---

### Post by wildmanne39 on 2011-09-19
Hi, that is a lot easier to read, thank you.

I just wanted to tell you I am looking up the driver you need and the procedure to install it so it is going to take a few minutes.
Thank you

---

### Post by wildmanne39 on 2011-09-19
Hi, all right I found the information, here is a link start with post 9, if you need more help post back here please.
[http://ubuntuforums.org/showthread.php?t=1740963](http://ubuntuforums.org/showthread.php?t=1740963)
Thank you

---

### Post by wildmanne39 on 2011-09-19
Hi, give me a minute I think I have more updated directions that are easier to use.
Thank you

---

### Post by hardisty on 2011-09-19
> **wildmanne39 said:**
> Hi, all right I found the information, here is a link start with post 9, if you need more help post back here please.
[http://ubuntuforums.org/showthread.php?t=1740963](http://ubuntuforums.org/showthread.php?t=1740963)
Thank you

Thanks for the help! I'm somewhat lost at

"Edit the config.mk file as below:
HAS_ATE=y (no change, it was originally as is)
HAS_WPA_SUPPLICANT=y (no change, it was originally as is)
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y (no change, it was originally as is)
HAS_ANTENNA_DIVERSITY_SUPPORT=y originally was n -- this was the only thing I modified)"

---

### Post by hardisty on 2011-09-19
got it! :)

---

### Post by wildmanne39 on 2011-09-19
Hi, I did find better directions one that driver that does not require the patch because of a newer driver.
The link is here start at 58.
[http://ubuntuforums.org/showthread.php?t=1779005&page=6](http://ubuntuforums.org/showthread.php?t=1779005&page=6)

Since you already started making that driver do this please make sure you are in the drivers directory then run these commands please.
```
sudo su
make clean
```
Then continue in the other link, compiling drivers can be a little complicated.
Thank you

---

### Post by hardisty on 2011-09-19
> **hardisty said:**
> got it! :)

The editing, that is, not the whole problem. The file doesn't have HAS_ANTENNA_DIVERSITY_SUPPORT, is that going to be a big problem?

---

### Post by wildmanne39 on 2011-09-19
Hi, let's see where we are at when you start compiling the new driver in the new link.
Thank you

---

### Post by hardisty on 2011-09-19
> **wildmanne39 said:**
> Hi, let's see where we are at when you start compiling the new driver in the new link.
Thank you

hadn't seen that part yet! thanks!

---

### Post by wildmanne39 on 2011-09-19
Hi, the link for the new driver is in post 58 of the second link I gave you.
Thank you

---

### Post by hardisty on 2011-09-19
Worked! Thanks so much!

---

### Post by wildmanne39 on 2011-09-19
Hi, that is great, I am glad I could help would you consider clicking on the red link in my signature and supporting me for ubuntu membership please? also would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by hardisty on 2011-09-20
> **wildmanne39 said:**
> Hi, that is great, I am glad I could help would you consider clicking on the red link in my signature and supporting me for ubuntu membership please? also would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.


Already did both of those things before you asked:cool:

---

### Post by wildmanne39 on 2011-09-20
Hi, I noticed that last night a little while after I posted the message.
Thank you):P

---

### Post by hardisty on 2011-11-13
I'm resurrecting this thread from "SOLVED" for two reasons, which I will state in a moment, please let me know if this is in bad form.

1. While this definitely made me able to connect to wireless, the strength became absolutely terrible and would drop the connection every couple of minutes. (I made a thread here [http://ubuntuforums.org/showthread.php?t=1862967](http://ubuntuforums.org/showthread.php?t=1862967)) I am wondering if there is something that I can do about this.

2. I have had to perform the fix in this thread about 3 times now, as it keeps randomly reverting back to how it was when I first posted. I cannot see any sort of pattern to what causes it to go back. I feel it may be worth noting that the physical wireless button on my keyboard causes the system to go to the next option in a cycle of 4 different settings. I cannot post the exact descriptions now because it is back to not working at all, but it would essentially be:

a) Light off, toolbar panel reads something like "No Connection"
b) Light off, reads "Wireless disabled by hardware switch"
c) Light on, reads something like "No Connection"
d) Light on, reads list of available connections.


Thanks to anybody who can provide assistance!

---

### Post by hardisty on 2011-11-13
It appears that I do not know how to make the thread no longer "SOLVED"

-- got it

---

### Post by hardisty on 2011-11-13
> **hardisty said:**
> I'm resurrecting this thread from "SOLVED" for two reasons, which I will state in a moment, please let me know if this is in bad form.

1. While this definitely made me able to connect to wireless, the strength became absolutely terrible and would drop the connection every couple of minutes. (I made a thread here [http://ubuntuforums.org/showthread.php?t=1862967](http://ubuntuforums.org/showthread.php?t=1862967)) I am wondering if there is something that I can do about this.

2. I have had to perform the fix in this thread about 3 times now, as it keeps randomly reverting back to how it was when I first posted. I cannot see any sort of pattern to what causes it to go back. I feel it may be worth noting that the physical wireless button on my keyboard causes the system to go to the next option in a cycle of 4 different settings. I cannot post the exact descriptions now because it is back to not working at all, but it would essentially be:

a) Light off, toolbar panel reads something like "No Connection"
b) Light off, reads "Wireless disabled by hardware switch"
c) Light on, reads something like "No Connection"
d) Light on, reads list of available connections.


Thanks to anybody who can provide assistance!


"No Connection" is actually "disconnected"

---

### Post by hardisty on 2011-11-14
Anyone? Should I make a new thread?

---

### Post by wildmanne39 on 2011-11-14
Hi, the reason you have to redo the procedure is because you installed the driver from an outside source so you will have to do that every time you have an update to your kernel.

I am not sure that I can help with disconnections but I will try.

Yes you probably should have started a new thread in networking on the disconnections since it is a different issue then the one you originally had and is has been a long time since it was solved.

I found a new way to install that driver so you will not have to redo it every time their is a kernel upgrade.

Change into the drivers directory then run these commands please:
```
sudo su
make clean
```
Then
Run these commands one line at a time please:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms patch fakeroot unzip
wget http://media.cdn.ubuntu-de.org/forum/attachments/3208747/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
unzip angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
cd angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/
sudo make
sudo make install
sudo modprobe -v rt5390sta
sudo depmod -a
sudo update-initramfs -u 
```
Then see how your disconnections are, they maybe be related to weak signal strength and their may not be anything we can do about that, but let me know after you run these commands.
Thank you

---

### Post by hardisty on 2011-11-21
> **wildmanne39 said:**
> Hi, the reason you have to redo the procedure is because you installed the driver from an outside source so you will have to do that every time you have an update to your kernel.

I am not sure that I can help with disconnections but I will try.

Yes you probably should have started a new thread in networking on the disconnections since it is a different issue then the one you originally had and is has been a long time since it was solved.

I found a new way to install that driver so you will not have to redo it every time their is a kernel upgrade.

Change into the drivers directory then run these commands please:
```
sudo su
make clean
```
Then
Run these commands one line at a time please:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms patch fakeroot unzip
wget http://media.cdn.ubuntu-de.org/forum/attachments/3208747/angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
unzip angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.zip
cd angepasster-2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/
sudo make
sudo make install
sudo modprobe -v rt5390sta
sudo depmod -a
sudo update-initramfs -u 
```
Then see how your disconnections are, they maybe be related to weak signal strength and their may not be anything we can do about that, but let me know after you run these commands.
Thank you

It doesn't fully kick me off and then on again, so I thank you very much for that. If there's a way I could use terminal to like, provide a two minute report of it's activity or something like that, I'll post it here. It's still fluctuating quite a bit between 1 and 4 bars

---

### Post by wildmanne39 on 2011-11-24
Hi, I am sorry but I am out of idea's.

---

