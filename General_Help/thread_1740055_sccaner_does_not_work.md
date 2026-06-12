---
title: "sccaner does not work"
date: 2011-04-26
forum: General Help
---

### Post by new-lin on 2011-04-26
I hav Plustek OpticPro 600P scanner plug in on to Ubuntu 10.04,
also I installed sane from Synaptic Package Manager.
There is file plustek_pp.conf ( /etc/sane.d/plustek_pp.conf ),
with nex content:

# Plustek-PP SANE Backend configuration file
# For use with Plustek parallel-port scanners 
#

#
# user either [direct] or [kernel] to access the scanner
# when using [kernel], device specifies the device-node, which is created
# by the kernel-module loader (applies only to Linux)
# when using [direct], device is used to set the parallel-port base address
# or a device-name suitable for libieee1284, i.e. parport0
#
#[direct]
#device 0x378

#
# example for accessing the scanner via libieee1284
#
[direct]
device parport0

#
# leave the default values as specified in /etc/modules.conf
#
option warmup    -1
option lOffOnEnd -1
option lampOff   -1

# model override switch, mostly for cosmetic changes, if the autodetection
# does not work or could not work correctly
#option mov 7

#
# example for accessing the scanner via the kernel module
#
#[kernel]
#device /dev/pt_drv
#
#option warmup    -1
#option lOffOnEnd -1
#option lampOff   -1

when I run command "sudo scanimage -L"
I get message: "device `plustek_pp:parport0' is a Plustek 600P/6000P flatbed scanner"

But when I tryed run Simple Scan I got nex message:

"No scanners detected"
"Please check your scanner is connected and powered on"

The device is plug in and bright. What is rong?

---

