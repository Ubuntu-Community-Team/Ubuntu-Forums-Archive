---
title: "usb devices won't work on inspiron 4150"
date: 2010-02-11
forum: General Help
---

### Post by mfrag on 2010-02-11
Hi All.  Need some help for a friend who recently bought an old laptop on ebay (an inspiron 4150).  It came with 9.10 installed and basically everything works.  However we can't get any usb flash drives to work or a usb mouse either.  This is her first experience with linux and I would like to get things working for her.  I don't think the one usb port is dead as the output of dmesg gives among other things:

```

.
.
.
[    0.306570] usbcore: registered new interface driver usbfs
[    0.306609] usbcore: registered new interface driver hub
[    0.306656] usbcore: registered new device driver usb
.
.
.
[    1.467394] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.467433] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.467460] uhci_hcd: USB Universal Host Controller Interface driver
[    1.467531] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    1.467545] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.467552] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.467649] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    1.467689] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[    1.467852] usb usb1: configuration #1 chosen from 1 choice
[    1.467912] hub 1-0:1.0: USB hub found
[    1.467929] hub 1-0:1.0: 2 ports detected
.
.
.
[    4.101341] Initializing USB Mass Storage driver...
[    4.101392] usbcore: registered new interface driver usb-storage
[    4.101398] USB Mass Storage support registered.
.
.
.

```

Running lspci returns among other things:

```

00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)

```

Here is the output of lsmod:

```

laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
arc4                    1660  2 
ecb                     2524  2 
p54pci                  9468  0 
p54common              26336  1 p54pci
led_class               4096  1 p54common
mac80211              181140  2 p54pci,p54common
cfg80211               93052  2 p54common,mac80211
joydev                 10240  0 
pcmcia                 36808  0 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
iptable_filter          3100  0 
snd_seq_dummy           2656  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
dell_wmi                2564  0 
dcdbas                  7292  0 
yenta_socket           24296  3 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                56500  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
serio_raw               5280  0 
shpchp                 32272  0 
ppdev                   6688  0 
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usb_storage            52576  0 
3c59x                  37636  0 
mii                     5212  1 3c59x
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
intel_agp              27484  1 
agpgart                34988  3 ttm,drm,intel_agp
floppy                 54916  0 
video                  19380  0 
output                  2780  1 video

```

Running lsusb returns:

```

Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

There is no change in the output of dmesg when I remove and reinsert a flash drive.  The light on the usb flash drive is coming on however.  I have tried a number of live cd's and have not been able to get anything out of this usb port.

Any bright ideas folks?  I would really appreciate some help.  I hope it is not dead.  If it is, does anyone have good things to say about using laptop pci usb cards?  Her wireless pci card is working just fine.

Thanks in advance for any help.
mfrag

---

### Post by iponeverything on 2010-02-11
My guess would be that it has a flaky usb port. The solder often comes loose from where the port connector attaches to the MB. 

If you bend the usb drive a bit up or down and stuff starts showing up in syslog or messages, you're probably just looking bad solder points.

---

### Post by mfrag on 2010-02-11
I was thinking it could be something like that.  I haven't checked yet, I may tonight if I get some time.  

However, I thought maybe the output from dmesg indicated it the port was good.  Plus, I'm getting power as the red light from the flash drive is on.

Also, I just got done playing around with a docking station that came with the laptop.  It has two usb ports in the back of it.  So, I thought, "problem solved!"  However, when we hook up the laptop to the docking station we still can't get anything to work in the additional usb ports???
Other things are working with the docking station however.

Any ideas?

---

### Post by mfrag on 2010-02-11
Maybe I'm making progress.  After putting the laptop into the docking station, I tried a usb keyboard and got the following from dmesg:

```

[  126.212138] usb 2-2: new low speed USB device using uhci_hcd and address 2
[  126.336125] usb 2-2: device descriptor read/64, error -71
[  126.564122] usb 2-2: device descriptor read/64, error -71
[  126.780151] usb 2-2: new low speed USB device using uhci_hcd and address 3
[  126.904125] usb 2-2: device descriptor read/64, error -71
[  127.132118] usb 2-2: device descriptor read/64, error -71
[  127.348122] usb 2-2: new low speed USB device using uhci_hcd and address 4
[  127.756120] usb 2-2: device not accepting address 4, error -71
[  127.868139] usb 2-2: new low speed USB device using uhci_hcd and address 5
[  128.276125] usb 2-2: device not accepting address 5, error -71
[  128.276161] hub 2-0:1.0: unable to enumerate USB device on port 2


```

Any ideas???

---

### Post by mfrag on 2010-02-21
I'm not convinced the USB ports are broken.  Nevertheless, an 8 dollar Dynex Notebook PCMCIA 2-Port USB 2.0 Card DX-UC202 allows me to use usb devices.  Not satisfactory, but it works.

---

