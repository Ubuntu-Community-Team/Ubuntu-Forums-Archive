---
title: "/dev/lp0 is missing..."
date: 2011-12-06
forum: General Help
---

### Post by AKADAP on 2011-12-06
I have a USB to Parallel port adapter that was working fine in 11.04. After upgrading to 11.10, the /dev/lp0 device or /dev/usb/lp0 device no longer gets created. This makes it impossible to print.

lsusb shows the parallel port along with the serial port on the same device, but although the /dev/serial gets created, there is nothing in /dev that looks anything like a parallel port.

---

### Post by AKADAP on 2011-12-07
A bit more info:
I now have two USB to parallel adapters plugged in. Both show up in lsusb
```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 002 Device 002: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 003 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 002 Device 004: ID 0424:2602 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 005: ID 045e:075d Microsoft Corp. LifeCam Cinema
Bus 002 Device 006: ID 03f0:0b01 Hewlett-Packard ScanJet 82x0C
Bus 002 Device 007: ID 0557:2213 ATEN International Co., Ltd CS682 2-Port USB 2.0 DVI KVM Switch
Bus 003 Device 003: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
Bus 003 Device 004: ID 1376:a001 Vimtron Electronics Co., Ltd. 
Bus 003 Device 005: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 002 Device 008: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 001 Device 004: ID 9710:7705 MosChip Semiconductor MCS7705 Parallel port adapter

```
Neither create /dev/lp or /dev/parallel. Also there is no /dev/usb directory.
```
$ ls /dev
autofs              tty18
block               tty19
bsg                 tty2
btrfs-control       tty20
bus                 tty21
cdrom               tty22
cdrw                tty23
char                tty24
console             tty25
core                tty26
cpu                 tty27
cpu_dma_latency     tty28
disk                tty29
dri                 tty3
dvb                 tty30
dvd                 tty31
dvdrw               tty32
ecryptfs            tty33
fb0                 tty34
fd                  tty35
fd0                 tty36
full                tty37
fuse                tty38
fw0                 tty39
hidraw0             tty4
hidraw1             tty40
hidraw2             tty41
hidraw3             tty42
hpet                tty43
input               tty44
kmsg                tty45
log                 tty46
loop0               tty47
loop1               tty48
loop2               tty49
loop3               tty5
loop4               tty50
loop5               tty51
loop6               tty52
loop7               tty53
mapper              tty54
mcelog              tty55
md                  tty56
md127               tty57
mem                 tty58
net                 tty59
network_latency     tty6
network_throughput  tty60
null                tty61
oldmem              tty62
port                tty63
ppp                 tty7
psaux               tty8
ptmx                tty9
pts                 ttyprintk
ram0                ttyS0
ram1                ttyS1
ram10               ttyS10
ram11               ttyS11
ram12               ttyS12
ram13               ttyS13
ram14               ttyS14
ram15               ttyS15
ram2                ttyS16
ram3                ttyS17
ram4                ttyS18
ram5                ttyS19
ram6                ttyS2
ram7                ttyS20
ram8                ttyS21
ram9                ttyS22
random              ttyS23
rfkill              ttyS24
rtc                 ttyS25
rtc0                ttyS26
scd0                ttyS27
sda                 ttyS28
sda1                ttyS29
sda2                ttyS3
sda5                ttyS30
sdb                 ttyS31
sdb1                ttyS4
sdb2                ttyS5
sdb5                ttyS6
sdc                 ttyS7
sdc1                ttyS8
sdd                 ttyS9
sdd1                ttyUSB0
sde                 uinput
sde1                urandom
sde2                usbmon0
sde5                usbmon1
sdf                 usbmon2
sdg                 usbmon3
serial              usbmon4
sg0                 usbmon5
sg1                 usbmon6
sg2                 usbmon7
sg3                 usbmon8
sg4                 v4l
sg5                 vbi0
sg6                 vcs
sg7                 vcs1
sg8                 vcs2
shm                 vcs3
snapshot            vcs4
snd                 vcs5
sr0                 vcs6
stderr              vcs7
stdin               vcsa
stdout              vcsa1
tty                 vcsa2
tty0                vcsa3
tty1                vcsa4
tty10               vcsa5
tty11               vcsa6
tty12               vcsa7
tty13               vga_arbiter
tty14               video0
tty15               video1
tty16               zero
tty17

```

Any other tools I should use to debug this?

---

