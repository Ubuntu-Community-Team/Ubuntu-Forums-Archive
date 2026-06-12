---
title: "Understanding RAW USB Input Data"
date: 2011-08-31
forum: General Help
---

### Post by TVLuke on 2011-08-31
Hello

I have a [Logitech K750 Keyboard]("http://www.logitech.com/keyboards/keyboard/devices/7454"), which is a wireless keyboard powered by two solar panels. From the windows application that can be downloaded I know, that the keyboard transmits the light intensity to the computer. It is, on a windows computer, displayed by the "[logitech Solar App]("http://www.logitech.com/en-us/68/8603")", if the light in the room changes, the App shows how many lux and if this is enough for the keyboard.

I would like to use the Keyboard as a lightsensor under Ubuntu in an effort to switch on the light in my office automatically when needed, and of when it is just a waste of energy.

The first step to be able to do so would be to get the data from the USB-receiver. The Receiver is a [Logitech Unifying Receiver]("http://www.logitech.com/en-us/349/6072?debug=0"), there is no second device attached to it.

I have tried to identifiy the USB ports where the data from my keyboard or my wireles mouse com in, but even with that I have mostly been unsucesful. Using cat /dev/hiddev0 (once i found my mouse on hiddev0 but could not reproduce this...) I do get Data that may be from the keyboard under "/dev/tty0" but this does not make any sense to me.

I Pipe the data into a ".txt" file

sudo cat /dev/tty0 >text.txt

it is a binary file, thus a text reader can not read it unless I use "od"

od -x text.txt

returns something like

0000000 1e9e b030 b030 2eae ae2e 9e1e 2030 00a0
0000017

(the keys pressed where aaabbbcccabcd)

If I repeat (with the same combination of keys), the data returned on tty0 is diferent, for example

0000000 301e 2eb0 aeae a01e 001d
0000011

I have no idea if this even has any connection to the keyboard (but as long as I do not press any keys, the file stays empty)

Some information on the usb-configuration: the last lines of the dmseg output are

[155001.940981] usb 5-2: new low speed USB device using uhci_hcd and address 7
[155002.156077] input: MLK wireless mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input15
[155002.156377] generic-usb 0003:046A:0106.0009: input,hiddev0,hidraw0: USB HID v1.10 Mouse [MLK wireless mouse] on usb-0000:00:1d.3-2/input0
[155007.848062] usb 5-1: new full speed USB device using uhci_hcd and address 8
[155008.060229] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input16
[155008.060429] generic-usb 0003:046D:C52B.000A: input,hidraw1: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.3-1/input0
[155008.066349] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.1/input/input17
[155008.066625] generic-usb 0003:046D:C52B.000B: input,hiddev0,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.3-1/input1
[155008.076067] generic-usb 0003:046D:C52B.000C: hiddev0,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.3-1/input2

and lsusb gives me 

Bus 005 Device 008: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 007: ID 046a:0106 Cherry GmbH 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ls -lt /dev

crw-rw-rw-  1 root tty       5,   2 2011-08-31 09:23 ptmx
crw-------  1 root root    251,   2 2011-08-31 09:21 hidraw2
crw-------  1 root root    251,   3 2011-08-31 09:21 hidraw3
drwxr-xr-x  2 root root         100 2011-08-31 09:21 usb
drwxr-xr-x  4 root root         380 2011-08-31 09:21 input
crw-------  1 root root    251,   1 2011-08-31 09:21 hidraw1
drwxr-xr-x  2 root root        4180 2011-08-31 09:21 char
crw-------  1 root root    251,   0 2011-08-31 09:21 hidraw0
crw-rw-rw-  1 root tty       5,   0 2011-08-31 09:19 tty
drwxrwxrwt  2 root root         200 2011-08-30 18:28 shm
crw-rw----  1 root tty       7, 141 2011-08-30 11:54 vcsa13
crw-rw----  1 root tty       7,  13 2011-08-30 11:54 vcs13
crw-rw----  1 root tty       7,  14 2011-08-30 11:54 vcs14
crw-rw----  1 root tty       7, 142 2011-08-30 11:54 vcsa14
crw-rw----  1 root tty       7,  15 2011-08-30 11:54 vcs15
crw-rw----  1 root tty       7, 143 2011-08-30 11:54 vcsa15
crw-rw----  1 root tty       7, 144 2011-08-30 11:54 vcsa16
crw-rw----  1 root tty       7,  16 2011-08-30 11:54 vcs16
crw-rw----  1 root tty       7,  17 2011-08-30 11:54 vcs17
crw-rw----  1 root tty       7, 145 2011-08-30 11:54 vcsa17
crw-rw----  1 root tty       7,  18 2011-08-30 11:54 vcs18
crw-rw----  1 root tty       7, 146 2011-08-30 11:54 vcsa18
crw-rw----  1 root tty       7,  19 2011-08-30 11:54 vcs19
crw-rw----  1 root tty       7, 147 2011-08-30 11:54 vcsa19
crw-rw----  1 root tty       7,  20 2011-08-30 11:54 vcs20
crw-rw----  1 root tty       7, 148 2011-08-30 11:54 vcsa20
drwxr-xr-x  2 root root         640 2011-08-29 16:17 block
drwxr-xr-x  5 root root         100 2011-08-29 16:17 disk
drwxr-xr-x  2 root root          80 2011-08-29 16:17 bsg
drwxr-xr-x  2 root root          60 2011-08-29 16:17 mapper
drwxr-xr-x  3 root root          60 2011-08-29 16:17 bus
drwxr-xr-x  2 root root          60 2011-08-29 16:17 pktcdvd
crw-------  1 root root      4,   1 2011-08-29 14:18 tty1
crw-------  1 root root      5,   1 2011-08-29 14:18 console
crw-rw----+ 1 root video    81,   0 2011-08-29 14:18 video0
crw-------  1 root root      4,   6 2011-08-29 14:18 tty6
crw-------  1 root root      4,   3 2011-08-29 14:18 tty3
crw-------  1 root root      4,   2 2011-08-29 14:18 tty2
crw-------  1 root root      4,   5 2011-08-29 14:18 tty5
crw-------  1 root root      4,   4 2011-08-29 14:18 tty4
crw-rw-rw-  1 root root    195,   0 2011-08-29 14:18 nvidia0
crw-rw-rw-  1 root root    195, 255 2011-08-29 14:18 nvidiactl
crw-rw----  1 root video    29,   0 2011-08-29 14:18 fb0
brw-rw----  1 root disk      8,   1 2011-08-29 14:18 sda1
srw-rw-rw-  1 root root           0 2011-08-29 14:18 log
lrwxrwxrwx  1 root root           4 2011-08-29 14:18 root -> sda5
brw-rw----  1 root disk      8,   2 2011-08-29 14:18 sda2
brw-rw----  1 root disk      8,   5 2011-08-29 14:18 sda5
brw-rw----  1 root disk      8,   6 2011-08-29 14:18 sda6
drwxr-xr-x  3 root root         180 2011-08-29 14:18 snd
brw-rw----  1 root disk      8,   0 2011-08-29 14:18 sda
lrwxrwxrwx  1 root root           3 2011-08-29 14:18 cdrom -> sr0
lrwxrwxrwx  1 root root           3 2011-08-29 14:18 cdrw -> sr0
lrwxrwxrwx  1 root root           3 2011-08-29 14:18 dvd -> sr0
lrwxrwxrwx  1 root root           3 2011-08-29 14:18 dvdrw -> sr0
lrwxrwxrwx  1 root root           3 2011-08-29 14:18 scd0 -> sr0
brw-rw----+ 1 root cdrom    11,   0 2011-08-29 14:18 sr0
brw-rw----  1 root disk      7,   2 2011-08-29 14:18 loop2
brw-rw----  1 root disk      7,   7 2011-08-29 14:18 loop7
crw-rw----  1 root tty       7,   5 2011-08-29 14:18 vcs5
crw-rw----  1 root tty       7, 133 2011-08-29 14:18 vcsa5
crw-rw----  1 root tty       7, 134 2011-08-29 14:18 vcsa6
brw-rw----  1 root disk      7,   0 2011-08-29 14:18 loop0
crw-rw----  1 root tty       7,   6 2011-08-29 14:18 vcs6
crw-rw----  1 root tty       7, 130 2011-08-29 14:18 vcsa2
crw-rw----  1 root tty       7,   2 2011-08-29 14:18 vcs2
crw-rw----  1 root tty       7,   3 2011-08-29 14:18 vcs3
crw-rw----  1 root tty       7,   4 2011-08-29 14:18 vcs4
crw-rw----  1 root tty       7, 131 2011-08-29 14:18 vcsa3
crw-rw----  1 root tty       7, 132 2011-08-29 14:18 vcsa4
brw-rw----  1 root disk      7,   5 2011-08-29 14:18 loop5
brw-rw----  1 root disk      7,   6 2011-08-29 14:18 loop6
brw-rw----  1 root disk      7,   3 2011-08-29 14:18 loop3
brw-rw----  1 root disk      7,   1 2011-08-29 14:18 loop1
brw-rw----  1 root disk      7,   4 2011-08-29 14:18 loop4
crw-rw----  1 root tty       7, 129 2011-08-29 14:18 vcsa1
crw-------  1 root root      5,   3 2011-08-29 14:18 ttyprintk
crw-------  1 root root    252,   0 2011-08-29 14:18 usbmon0
crw-rw----  1 root tty       7,   0 2011-08-29 14:18 vcs
crw-rw----  1 root tty       7,   1 2011-08-29 14:18 vcs1
crw-rw----  1 root tty       7, 128 2011-08-29 14:18 vcsa
crw--w----  1 root tty       4,  63 2011-08-29 14:18 tty63
crw--w----  1 root tty       4,   7 2011-08-29 14:18 tty7
crw--w----  1 root tty       4,   8 2011-08-29 14:18 tty8
crw--w----  1 root tty       4,   9 2011-08-29 14:18 tty9
crw--w----  1 root tty       4,  60 2011-08-29 14:18 tty60
crw--w----  1 root tty       4,  61 2011-08-29 14:18 tty61
crw--w----  1 root tty       4,  62 2011-08-29 14:18 tty62
crw--w----  1 root tty       4,  56 2011-08-29 14:18 tty56
crw--w----  1 root tty       4,  57 2011-08-29 14:18 tty57
crw--w----  1 root tty       4,  58 2011-08-29 14:18 tty58
crw--w----  1 root tty       4,  59 2011-08-29 14:18 tty59
crw--w----  1 root tty       4,  52 2011-08-29 14:18 tty52
crw--w----  1 root tty       4,  53 2011-08-29 14:18 tty53
crw--w----  1 root tty       4,  54 2011-08-29 14:18 tty54
crw--w----  1 root tty       4,  55 2011-08-29 14:18 tty55
crw-rw----+ 1 root cdrom    21,   0 2011-08-29 14:18 sg0
crw--w----  1 root tty       4,  51 2011-08-29 14:18 tty51
crw--w----  1 root tty       4,  50 2011-08-29 14:18 tty50
crw--w----  1 root tty       4,  49 2011-08-29 14:18 tty49
crw--w----  1 root tty       4,  47 2011-08-29 14:18 tty47
crw--w----  1 root tty       4,  48 2011-08-29 14:18 tty48
crw--w----  1 root tty       4,  42 2011-08-29 14:18 tty42
crw--w----  1 root tty       4,  43 2011-08-29 14:18 tty43
crw--w----  1 root tty       4,  44 2011-08-29 14:18 tty44
crw--w----  1 root tty       4,  45 2011-08-29 14:18 tty45
crw--w----  1 root tty       4,  46 2011-08-29 14:18 tty46
crw--w----  1 root tty       4,  39 2011-08-29 14:18 tty39
crw--w----  1 root tty       4,  40 2011-08-29 14:18 tty40
crw--w----  1 root tty       4,  41 2011-08-29 14:18 tty41
crw--w----  1 root tty       4,  35 2011-08-29 14:18 tty35
crw--w----  1 root tty       4,  36 2011-08-29 14:18 tty36
crw--w----  1 root tty       4,  37 2011-08-29 14:18 tty37
crw--w----  1 root tty       4,  38 2011-08-29 14:18 tty38
crw--w----  1 root tty       4,  31 2011-08-29 14:18 tty31
crw--w----  1 root tty       4,  32 2011-08-29 14:18 tty32
crw--w----  1 root tty       4,  33 2011-08-29 14:18 tty33
crw--w----  1 root tty       4,  34 2011-08-29 14:18 tty34
crw--w----  1 root tty       4,  28 2011-08-29 14:18 tty28
crw--w----  1 root tty       4,  29 2011-08-29 14:18 tty29
crw--w----  1 root tty       4,  30 2011-08-29 14:18 tty30
crw--w----  1 root tty       4,  24 2011-08-29 14:18 tty24
crw--w----  1 root tty       4,  25 2011-08-29 14:18 tty25
crw--w----  1 root tty       4,  26 2011-08-29 14:18 tty26
crw--w----  1 root tty       4,  27 2011-08-29 14:18 tty27
crw--w----  1 root tty       4,  20 2011-08-29 14:18 tty20
crw--w----  1 root tty       4,  21 2011-08-29 14:18 tty21
crw--w----  1 root tty       4,  22 2011-08-29 14:18 tty22
crw--w----  1 root tty       4,  23 2011-08-29 14:18 tty23
crw--w----  1 root tty       4,  17 2011-08-29 14:18 tty17
crw--w----  1 root tty       4,  18 2011-08-29 14:18 tty18
crw--w----  1 root tty       4,  19 2011-08-29 14:18 tty19
crw--w----  1 root tty       4,  13 2011-08-29 14:18 tty13
crw--w----  1 root tty       4,  14 2011-08-29 14:18 tty14
crw--w----  1 root tty       4,  15 2011-08-29 14:18 tty15
crw--w----  1 root tty       4,  16 2011-08-29 14:18 tty16
crw--w----  1 root tty       4,  10 2011-08-29 14:18 tty10
crw--w----  1 root tty       4,  11 2011-08-29 14:18 tty11
crw--w----  1 root tty       4,  12 2011-08-29 14:18 tty12
brw-rw----  1 root disk      1,   8 2011-08-29 14:18 ram8
brw-rw----  1 root disk      1,   9 2011-08-29 14:18 ram9
brw-rw----  1 root disk      1,   6 2011-08-29 14:18 ram6
brw-rw----  1 root disk      1,   7 2011-08-29 14:18 ram7
brw-rw----  1 root disk      1,   4 2011-08-29 14:18 ram4
brw-rw----  1 root disk      1,   5 2011-08-29 14:18 ram5
brw-rw----  1 root disk      1,   2 2011-08-29 14:18 ram2
brw-rw----  1 root disk      1,   3 2011-08-29 14:18 ram3
brw-rw----  1 root disk      1,  14 2011-08-29 14:18 ram14
brw-rw----  1 root disk      1,  15 2011-08-29 14:18 ram15
brw-rw----  1 root disk      1,  12 2011-08-29 14:18 ram12
brw-rw----  1 root disk      1,  13 2011-08-29 14:18 ram13
brw-rw----  1 root disk      1,  10 2011-08-29 14:18 ram10
brw-rw----  1 root disk      1,  11 2011-08-29 14:18 ram11
brw-rw----  1 root disk      1,   0 2011-08-29 14:18 ram0
brw-rw----  1 root disk      1,   1 2011-08-29 14:18 ram1
crw--w----  1 root tty       4,   0 2011-08-29 14:18 tty0
crw-------  1 root root    108,   0 2011-08-29 14:18 ppp
crw-rw----  1 root dialout   4,  71 2011-08-29 14:18 ttyS7
crw-------  1 root root     10,  63 2011-08-29 14:18 vga_arbiter
crw-rw----  1 root dialout   4,  72 2011-08-29 14:18 ttyS8
crw-r-----  1 root root     10, 223 2011-08-29 14:18 uinput
crw-------  1 root root     10,   1 2011-08-29 14:18 psaux
crw-rw-r--+ 1 root root     10,  62 2011-08-29 14:18 rfkill
crw-------  1 root root     10, 231 2011-08-29 14:18 snapshot
crw-------  1 root root     10, 228 2011-08-29 14:18 hpet
crw-------  1 root root     10, 227 2011-08-29 14:18 mcelog
crw-------  1 root root     10,  58 2011-08-29 14:18 network_latency
crw-------  1 root root     10,  57 2011-08-29 14:18 network_throughput
crw-------  1 root root     10,  59 2011-08-29 14:18 cpu_dma_latency
crw-------  1 root root     10,  61 2011-08-29 14:18 ecryptfs
crw-rw-rw-  1 root fuse     10, 229 2011-08-29 14:18 fuse
crw-rw-rw-  1 root root      1,   5 2011-08-29 14:18 zero
crw-------  1 root root      1,  12 2011-08-29 14:18 oldmem
crw-r-----  1 root kmem      1,   4 2011-08-29 14:18 port
crw-rw-rw-  1 root root      1,   8 2011-08-29 14:18 random
crw-rw-rw-  1 root root      1,   9 2011-08-29 14:18 urandom
crw-rw-rw-  1 root root      1,   7 2011-08-29 14:18 full
crw-------  1 root root      1,  11 2011-08-29 14:18 kmsg
crw-r-----  1 root kmem      1,   1 2011-08-29 14:18 mem
crw-rw-rw-  1 root root      1,   3 2011-08-29 14:18 null
crw-rw----  1 root disk     21,   1 2011-08-29 14:18 sg1
crw-rw----  1 root dialout   4,  73 2011-08-29 14:18 ttyS9
crw-rw----  1 root dialout   4,  70 2011-08-29 14:18 ttyS6
crw-rw----  1 root dialout   4,  95 2011-08-29 14:18 ttyS31
crw-rw----  1 root dialout   4,  68 2011-08-29 14:18 ttyS4
crw-rw----  1 root dialout   4,  69 2011-08-29 14:18 ttyS5
crw-rw----  1 root dialout   4,  67 2011-08-29 14:18 ttyS3
crw-rw----  1 root dialout   4,  94 2011-08-29 14:18 ttyS30
crw-rw----  1 root dialout   4,  91 2011-08-29 14:18 ttyS27
crw-rw----  1 root dialout   4,  92 2011-08-29 14:18 ttyS28
crw-rw----  1 root dialout   4,  93 2011-08-29 14:18 ttyS29
crw-rw----  1 root dialout   4,  88 2011-08-29 14:18 ttyS24
crw-rw----  1 root dialout   4,  89 2011-08-29 14:18 ttyS25
crw-rw----  1 root dialout   4,  90 2011-08-29 14:18 ttyS26
crw-rw----  1 root dialout   4,  82 2011-08-29 14:18 ttyS18
crw-rw----  1 root dialout   4,  83 2011-08-29 14:18 ttyS19
crw-rw----  1 root dialout   4,  84 2011-08-29 14:18 ttyS20
crw-rw----  1 root dialout   4,  85 2011-08-29 14:18 ttyS21
crw-rw----  1 root dialout   4,  86 2011-08-29 14:18 ttyS22
crw-rw----  1 root dialout   4,  87 2011-08-29 14:18 ttyS23
crw-rw----  1 root dialout   4,  75 2011-08-29 14:18 ttyS11
crw-rw----  1 root dialout   4,  76 2011-08-29 14:18 ttyS12
crw-rw----  1 root dialout   4,  77 2011-08-29 14:18 ttyS13
crw-rw----  1 root dialout   4,  78 2011-08-29 14:18 ttyS14
crw-rw----  1 root dialout   4,  79 2011-08-29 14:18 ttyS15
crw-rw----  1 root dialout   4,  80 2011-08-29 14:18 ttyS16
crw-rw----  1 root dialout   4,  81 2011-08-29 14:18 ttyS17
crw-rw----  1 root dialout   4,  66 2011-08-29 14:18 ttyS2
crw-rw----  1 root dialout   4,  64 2011-08-29 14:18 ttyS0
crw-rw----  1 root dialout   4,  65 2011-08-29 14:18 ttyS1
crw-rw----  1 root dialout   4,  74 2011-08-29 14:18 ttyS10
lrwxrwxrwx  1 root root           4 2011-08-29 14:18 rtc -> rtc0
crw-------  1 root root    254,   0 2011-08-29 14:18 rtc0
crw-------  1 root root    252,   5 2011-08-29 14:18 usbmon5
crw-------  1 root root    252,   1 2011-08-29 14:18 usbmon1
crw-------  1 root root    252,   4 2011-08-29 14:18 usbmon4
crw-------  1 root root    252,   2 2011-08-29 14:18 usbmon2
crw-------  1 root root    252,   3 2011-08-29 14:18 usbmon3
crw-------  1 root root     10, 235 2011-08-29 14:18 autofs
crw-------  1 root root     10, 234 2011-08-29 14:18 btrfs-control
lrwxrwxrwx  1 root root          11 2011-08-29 14:18 core -> /proc/kcore
drwxr-xr-x  2 root root          60 2011-08-29 14:18 cpu
lrwxrwxrwx  1 root root          13 2011-08-29 14:18 fd -> /proc/self/fd
lrwxrwxrwx  1 root root          15 2011-08-29 14:18 stderr -> /proc/self/fd/2
lrwxrwxrwx  1 root root          15 2011-08-29 14:18 stdin -> /proc/self/fd/0
lrwxrwxrwx  1 root root          15 2011-08-29 14:18 stdout -> /proc/self/fd/1
drwxr-xr-x  2 root root          60 2011-08-09 13:44 net
drwxr-xr-x  2 root root           0 2010-09-24 14:25 pts

---

### Post by TVLuke on 2011-08-31
Addition. I just found, that using dd instead of cat is most useful. Still, the data makes only little sense to me, but there now seems to be some kind of connections between the keys pressed and the data.

---

### Post by TVLuke on 2011-08-31
OK, the output is still somewhat confusing but 1e9c seems to (usually, not alwys) correspond to an "a", b030 (usually) to a "b" and so on. However, no additional data seems to be present that would indikate the light level.

sudo dd if=/dev/tty0 of=text6.txt bs=4k

the key that activates the App under windows does not seem to generate any kind of data on the usb when pressed (or I haven't figured it out yet)

asdasdasdasdasd corresponds to

0000000 1e9c 1f9e 209f 1ea0 1f9e 209f 1ea0 1f9e
0000020 209f 1ea0 1f9e 209f 1ea0 9f1f a020 2e1d
0000040

The 1e9c might be the enter key after I use "sudo dd if=/dev/tty0 of=text6.txt bs=4k"

---

