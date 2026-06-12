---
title: "Constantly having to restart wireless adapter"
date: 2011-11-16
forum: General Help
---

### Post by layers on 2011-11-16
So, I wrote this thread over the networking forum, but it's a dead place. The general section has much more able "support".

So, this happens only with the router at home - very often, every 5 min the internet connection is gone. I'm not kicked out of the network, nothing, just no internet. The way I fix it, I switch the wireless off and on, and after it connects, it's all good. for 5 mins...

This happens only at home, 2 different routers. It happens much less in other distros.

Is there a way to install different program or drivers that handle the wireless? I tried booting into Fedora, and it all works there, no problem.
In ubuntu, it usually happens only on my home router, when i try to download a file or load a site with a few images. I have no idea why it is happening. Does anyone have seen anything like this?

Is it the Ubuntu, or the laptop, or the router?

I'm really tired of this. Is is possible that I am overloading the router, so it stops giving me internet? And when i restart my wireless adapter on my laptop, it resets its connection, so internet is back? I don't really know what to think...

---

### Post by TBABill on 2011-11-16
Could be more than 1 driver wanting to control the adapter, something mis-configured, etc. Can you paste back here the output of the following in a terminal: ```
lspci
lsmod
```

---

### Post by layers on 2011-11-16
let's see...
can you explain what we're trying to look at?

> ibo@ibo-VPCF130FD:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1c.6 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller
03:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller
03:00.3 FireWire (IEEE 1394): Ricoh Co Ltd FireWire Host Controller
03:00.4 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8057 PCI-E Gigabit Ethernet Controller (rev 10)
05:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ibo@ibo-VPCF130FD:~$ lsmod
Module                  Size  Used by
btrfs                 550457  0 
zlib_deflate           27074  1 btrfs
libcrc32c              12644  1 btrfs
ufs                    75815  0 
qnx4                   17685  0 
hfsplus                84797  0 
hfs                    54731  0 
minix                  36367  0 
ntfs                  101769  0 
vfat                   21708  0 
msdos                  17333  0 
fat                    61374  2 vfat,msdos
jfs                   182186  0 
xfs                   823190  0 
exportfs               12998  1 xfs
reiserfs              248223  0 
parport_pc             36959  0 
ppdev                  17113  0 
binfmt_misc            17565  1 
pci_stub               12622  1 
vboxpci                23190  0 
vboxnetadp             13382  0 
vboxnetflt             23435  0 
vboxdrv               286726  3 vboxpci,vboxnetadp,vboxnetflt
snd_hda_codec_hdmi     28167  4 
rfcomm                 47694  10 
sco                    18187  2 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
btusb                  18600  2 
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
snd_hda_codec_realtek   336771  1 
uvcvideo               72195  0 
snd_hda_intel          33176  2 
arc4                   12529  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
joydev                 17606  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
nvidia              10709116  54 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 118238  0 
mac80211              294370  1 ath9k
ath9k_common           13851  1 ath9k
ath9k_hw              323077  2 ath9k,ath9k_common
ath                    23773  2 ath9k,ath9k_hw
cfg80211              178528  3 ath9k,mac80211,ath
psmouse                73535  0 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13166  0 
intel_ips              18097  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sony_laptop            39880  0 
video                  19438  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
usb_storage            53538  0 
hid                    91020  1 usbhid
uas                    17996  0 
ahci                   25951  4 
firewire_ohci          40370  0 
libahci                26642  1 ahci
xhci_hcd               77643  0 
sky2                   58509  0 
sdhci_pci              13989  0 
firewire_core          62646  1 firewire_ohci
sdhci                  27387  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
ibo@ibo-VPCF130FD:~$

---

