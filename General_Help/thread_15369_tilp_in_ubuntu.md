---
title: "tilp in ubuntu"
date: 2005-02-14
forum: General Help
---

### Post by KLineD on 2005-02-14
I've been trying to get my TI-89 to work with ubuntu, I installed tilp using apt with no errors, but when I go to the communications setup window and set the options to Silverlink (I have an USB cable) and port 1 with the TI-89 selected I get the following error:
> ticables: getting method from resources (automatic):
ticables:   check for tiusb usability:
ticables:     using devfs: no
ticables:     node /dev/tiusb0: does not exists
ticables:     => you will have to create the node.
ticables:   warning: can't use IO_TIUSB
ticables:   check for lib-usb usability:
ticables:     usb filesystem (/proc/bus/usb): mounted
ticables:     node /proc/bus/usb/devices: exists
ticables:     permissions/user/group: -rw-rw-r-- root root
ticables:     is user can r/w on device: yes
ticables: mapping I/O...
ticables: registering cable...
ticables: list of settings:
ticables:   cable: SilverLink
ticables:   port: USB port #1
ticables:   method: user mode (ioctl)
ticables:   device name: /dev/tiusb0
ticables:   delay value: 10
tifiles : settings:
tifiles :   calc type: TI89
ticalcs : settings:
ticalcs :   calc type: TI89
ticables: Found <SilverLink>.
ticables: err: usb_claim_interface (could not claim interface 0: Device or resource busy)

I know the cable works because I can use it in windows with the ti-connect software. Also I'm launching tilp as root. Any ideas?

---

### Post by KLineD on 2005-02-14
I have found what's wrong. From reading this site [here](http://evan.mcnabbs.org/linux-oss/ticalc/) I just followed the instructions:

> sudo mknod /dev/tiusb0 c 115 16
sudo chmod 666 /dev/tiusb0

Apparently the problem has to do with ubuntu using udev and tilp doesn't support this (similar to the minor problem when running vmware) so one has to create the device by hand.

Hope this helps.

---

### Post by nrayever on 2005-05-21
indeed this is the solucion, thanks a lot man!!!

---

