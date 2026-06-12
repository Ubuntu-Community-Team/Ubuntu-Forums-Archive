---
title: "Fresco Logic USB 3.0 not working"
date: 2012-01-11
forum: General Help
---

### Post by matt17y on 2012-01-11
Hi.  I have an Asrock 770extreme motherboard with onboard Fresco Logic USB 3.0.  I have been unable to get this working under Ubuntu 11.10.  The port works fine under Windows 7 with the Fresco Logic drivers installed.  When I connect and power on my external drive under ubuntu, absolutely nothing happens and the drive apparently isn't recognized.
Any suggestions??
I have tried adding pci=nomsi to /etc/default/grub and did sudo update-grub.  After a reboot the issue still remains.
Thanks. 

lspci

00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:05.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port B)
00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
02:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
03:00.0 IDE interface: Marvell Technology Group Ltd. Device 914d (rev 10)
04:00.0 USB Controller: Fresco Logic FL1000G USB 3.0 Host Controller (rev 01)
05:06.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)

---

### Post by Buntumatic on 2012-01-11
Is [COLOR="Blue"]xhci_hcd[/COLOR] loaded?

---

### Post by matt17y on 2012-01-11
I think so.  Here is my lsmod output

Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  4 
nvidia              10390874  40 
joydev                 17393  0 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          28358  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                63474  0 
serio_raw              12990  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
wmi                    18744  0 
k10temp                12990  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
i2c_piix4              13093  0 
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  0 
uas                    17699  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
sata_via               13534  0 
xhci_hcd               77120  0 
r8169                  47200  0 
pata_atiixp            12967  0 
ahci                   21634  2 
libahci                25761  1 ahci

---

### Post by matt17y on 2012-01-12
Does anyone else have any ideas?  I really would like to solve this issue once and for all since i have recently purchased a usb 3.0 enclosure for my 2tb drive.

---

### Post by matt17y on 2012-01-13
Just an update.  Tried upgrading from stock kernel 3.0.0.14 to kernel 3.1.4 with no success.. The port still refuses to work, both with and without adding pci=nomsi to grub config.  Dmesg | grep xhci says Timeout while waiting for a slot .. or something like that.  This is 32 bit Ubuntu 11.10.

Also, I booted a live cd of Ubuntu 10.10 I had lying around. The port would not work there either.

Has anyone had success with Fresco Logic FL1000G Rev 1?  Google searching gives me very few suggestions; all of which I have tried to no avail.

---

### Post by matt17y on 2012-01-19
I have decided to give up on using this usb 3.0 port under linux..  It appears I have tried about everything that I can find suggested on the forums and google.  Linux may be the first OS with usb 3.0 support but, currently, it appears to be pretty shoddy to me at best. It's hit or miss depending on which usb 3 device you have.  I will keep trying future releases to see if the issue is resolved.

---

### Post by Buntumatic on 2012-01-19
Looks like someone made it work by loading xhci early in boot process, maybe it means if uhci/ehci are loaded before xhci they cause a conflict. You could try:
1. the trick with initrd; [http://forums.opensuse.org/english/get-technical-help-here/hardware/464501-usb3-hd-not-detected.html](http://forums.opensuse.org/english/get-technical-help-here/hardware/464501-usb3-hd-not-detected.html)
2. or build a custom kernel with xhci built in;
3. or create a modprobe rule that loads xhci first.

---

### Post by matt17y on 2012-01-21
First of all, thank you for your attempts to help me.  What I have done is add 
xhci-hcd to /etc/modules, 
and then I created a file at /etc/modprobe.d/usb3 and added
softdep ehci-hcd pre: xhci-hcd
softdep uhci-hcd pre: ehci-hcd
softdep ohci-hcd pre: ehci-hcd

Is this the correct procedure?  I have no idea if I did the correct thing here in order to get xhci module to load first.  I can say that the above did not get USB working either though.

---

