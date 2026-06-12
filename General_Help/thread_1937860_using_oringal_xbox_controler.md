---
title: "using oringal xbox controler"
date: 2012-03-08
forum: General Help
---

### Post by EddDoubleD on 2012-03-08
I have a xbox controller to usb adapter and I want to use it in ubuntu 11.0. I heard something about xboxdrv but I don't know how to install it.
[http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

---

### Post by x1a4 on 2012-03-09
From the page referenced in your post

> 
Prebuild official binary packages are available for Ubuntu 11.04 and Ubuntu 10.04 LTS can be obtained from the PPA. To automatically add the repository to the sources.list and install xboxdrv use:

```

sudo add-apt-repository ppa:grumbel/ppa
sudo apt-get update
sudo apt-get install xboxdrv
sudo apt-get install xboxdrv-stable

```

Note that there are two xboxdrv packages in the repository, the xboxdrv package is the latest version, with the most features, but also potentially bugs and issues. The xboxdrv-stable package is simply an older version of xboxdrv for which no critical bugs are know.


If you're not comfortable in a terminal, install the package using Synaptic.  Just add the repo first.  


P.S.  Please don't bump so often.

---

### Post by EddDoubleD on 2012-03-09
-- [ ERROR ] ------------------------------------------------------
No Xbox or Xbox360 controller found

---

### Post by EddDoubleD on 2012-03-09
when I plug it up to my windows machine it just comes up as a generic hub

---

### Post by EddDoubleD on 2012-03-10
one bump a day

---

### Post by lrgmmc on 2012-03-10
what about ```
lsusb
```in terminal? Does it show up?

---

### Post by lrgmmc on 2012-03-10
after going through the man pages it looks like you need to run the app from terminal. its not automatically loaded. so in terminal run this while the controller is plugged in```
xboxdrv --list-controller
``` that should tell you if the driver is seeing anything.

---

### Post by EddDoubleD on 2012-03-10
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 002: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 004 Device 002: ID ffff:ffff  
Bus 004 Device 003: ID ffff:ffff

---

### Post by lrgmmc on 2012-03-10
what about the other code?```
xboxdrv --list-controller
```

---

### Post by EddDoubleD on 2012-03-10
says there is no controller

---

### Post by EddDoubleD on 2012-03-10
I'm using something like this to connect the controller 
[http://ecx.images-amazon.com/images/I/31VMg67GbmL._SL500_AA300_.jpg](http://ecx.images-amazon.com/images/I/31VMg67GbmL._SL500_AA300_.jpg)

---

### Post by lrgmmc on 2012-03-10
ok new plan. :D unplug the adaptor and controller from your pc. wait about 20 seconds, then plug both back in. In terminal run ```
dmesg |tail
``` post the output.

---

### Post by EddDoubleD on 2012-03-21
[   30.864676] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   31.220579] init: plymouth-stop pre-start process (1345) terminated with status 1
[   32.607317] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   36.928028] eth0: no IPv6 routers present
[ 6829.588020] usb 4-2: new full speed USB device number 2 using uhci_hcd
[ 6829.739113] hub 4-2:1.0: USB hub found
[ 6829.741836] hub 4-2:1.0: 3 ports detected
[ 6830.021931] usb 4-2.1: new full speed USB device number 3 using uhci_hcd
[ 6830.281186] input: Chinese-made Xbox Controller as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2.1/4-2.1:1.0/input/input4
[ 6830.281676] usbcore: registered new interface driver xpad

---

### Post by EddDoubleD on 2012-03-22
sorry for being a week late

---

### Post by EddDoubleD on 2012-03-24
a bump a day

---

### Post by EddDoubleD on 2012-03-25
bump

---

### Post by EddDoubleD on 2012-03-26
bump

---

### Post by lrgmmc on 2012-04-02
from that output it looks as if its getting recognized. I'll do some fishing around and see.  have a look here and see if any of it helps.[http://ubuntuforums.org/showthread.php?t=338457]("http://ubuntuforums.org/showthread.php?t=338457")

---

### Post by EddDoubleD on 2012-04-03
thanks

---

### Post by PRAEst76 on 2013-03-09
I have the same issue here. Was any resolution found?

Dmesg shows the following. I have the same adaptor as the OP so I'm thinking it's just a naff bit of hardware. Perhaps wired-up badly.


```
[ 2505.012032] usb 2-1: new full-speed USB device number 28 using uhci_hcd
[ 2505.160076] usb 2-1: New USB device found, idVendor=ffff, idProduct=ffff
[ 2505.160083] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 2505.163146] hub 2-1:1.0: USB hub found
[ 2505.165065] hub 2-1:1.0: 3 ports detected
[ 2505.445082] usb 2-1.1: new full-speed USB device number 29 using uhci_hcd
[ 2505.551089] usb 2-1.1: New USB device found, idVendor=ffff, idProduct=ffff
[ 2505.551096] usb 2-1.1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 2505.554233] input: Chinese-made Xbox Controller as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input24
[ 2511.446293] usb 2-1.1: USB disconnect, device number 29
[ 2511.568046] usb 2-1: reset full-speed USB device number 28 using uhci_hcd
[ 2511.688040] usb 2-1: device descriptor read/64, error -71
[ 2511.912116] usb 2-1: device descriptor read/64, error -71
[ 2512.128037] usb 2-1: reset full-speed USB device number 28 using uhci_hcd
[ 2512.248040] usb 2-1: device descriptor read/64, error -71
[ 2512.472028] usb 2-1: device descriptor read/64, error -71
[ 2512.688032] usb 2-1: reset full-speed USB device number 28 using uhci_hcd
[ 2513.096020] usb 2-1: device not accepting address 28, error -71
[ 2513.208044] usb 2-1: reset full-speed USB device number 28 using uhci_hcd
[ 2513.616024] usb 2-1: device not accepting address 28, error -71
[ 2513.720024] hub 2-1:1.0: hub_port_status failed (err = -19)
[ 2513.720033] hub 2-1:1.0: hub_port_status failed (err = -19)
[ 2513.720037] hub 2-1:1.0: hub_port_status failed (err = -19)
[ 2513.720041] hub 2-1:1.0: activate --> -19
[ 2513.720064] usb 2-1: USB disconnect, device number 28
[ 2513.960043] usb 2-1: new full-speed USB device number 30 using uhci_hcd
[ 2514.080037] usb 2-1: device descriptor read/64, error -71
[ 2514.304034] usb 2-1: device descriptor read/64, error -71
[ 2514.520037] usb 2-1: new full-speed USB device number 31 using uhci_hcd
[ 2514.640028] usb 2-1: device descriptor read/64, error -71
[ 2514.864041] usb 2-1: device descriptor read/64, error -71
[ 2515.080046] usb 2-1: new full-speed USB device number 32 using uhci_hcd
[ 2515.488033] usb 2-1: device not accepting address 32, error -71
[ 2515.600035] usb 2-1: new full-speed USB device number 33 using uhci_hcd
[ 2516.009462] usb 2-1: device not accepting address 33, error -75
[ 2516.009492] hub 2-0:1.0: unable to enumerate USB device on port 1

```

---

### Post by lrgmmc on 2013-03-09
I'm Not at home at this moment. Should be back in a few hours. When I do, I'll look over the thread and try to help.

---

