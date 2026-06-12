---
title: "Apple IR remote + Twisted Melon Manta receiver"
date: 2012-05-19
forum: General Help
---

### Post by Shplad on 2012-05-19
Hi all:

I have a little experience installing and running Ubuntu 11.1. 
I used to be a technician who worked with Windows all day, so basic computing concepts are familiar.
I'm trying to configure an Apple (v. 2 aka model 1294) IR remote control with a Twisted Melon Manta IR receiver on my HTPC.

My config:
======
-**Shuttle** SP35P2Pro runnning Ubuntu 11.1 (without patches). 
-Kernel: 3.0.0-15-generic-pae
-lirc is version 0.9.0Ubuntu

I  know the remote/receiver combination works, because pressing buttons  on the remote yields scancodes on the screen using "ir-keytable -t"  (but not using irw). However, I'm not sure it sends the right   scancodes. I have put a .conf file for the correct Apple remote in the /etc/lirc folder. I have put an include statement in the lircd.conf file which points to the Apple remote .conf file. 

dmesg info:
```

[   17.608033] Registered IR keymap rc-rc6-mce
[    17.608158] input: Media Center Ed. eHome Infrared Remote Transceiver  (147a:e03a) as  /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/rc/rc0/input5
[    17.608234] rc0: Media Center Ed. eHome Infrared Remote Transceiver  (147a:e03a) as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/rc/rc0
[   17.608308] mceusb 3-1:1.0: Registered Formosa21 eHome Infrared Transceiver on usb3:2
[   17.608352] usbcore: registered new interface driver mceusb
[   17.662530] nvidia: module license 'NVIDIA' taints kernel.
[   17.662535] Disabling lock debugging due to kernel taint
[   17.741453] IR NEC protocol handler initialized
.
.
.
[   18.629948] IR RC5(x) protocol handler initialized
[   18.668728] IR RC6 protocol handler initialized
[   18.704512] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   18.704516] hda_intel: Disabling MSI
[   18.704549] HDA Intel 0000:01:00.1: setting latency timer to 64
[   18.734797] IR JVC protocol handler initialized
[   18.796475] IR Sony protocol handler initialized
[   18.997566] lirc_dev: IR Remote Control driver registered, major 249 
[   18.998290] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[   18.998292] IR LIRC bridge handler initialized
[   19.828376] init: Failed to spawn smbd main process: unable to execute: No such file or directory


```lsusb info:
```

Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x147a Formosa Industrial Computing, Inc.
  idProduct          0xe03a eHome Infrared Receiver
  bcdDevice           11.12
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
 

```Can anyone answer a few questions I have:

1. Since I'm only getting scancodes using ir-keytable and not in irw, I assume this means that it's the newer in-kernel IR support that's working? 

I don't want to go and configure all kinds of lirc files if that can conflict with the in-kernel ir_core suppport.

2. If the above assumption is correct, what apps in Ubuntu 11.1 that will allow me to try IR remote support ? 
The remote didn't seem to work with music player. 

Do apps need to be manually configured to work even after ir-keytable shows keypresses or is having them work with ir-keytable
or irw enough?


3. Ultimately, my goal is to get the remote to work with Boxee 0.9x . Is that a separate task from just getting it working in Ubuntu? I tried to read through the Boxee documentation and forums, but could mostly find people who were using an Apple remote on an Apple product (different receiver) or on Macintosh.




Thanks in advance for any help.

---

