---
title: "USB external hard drive not recognized"
date: 2009-09-02
forum: General Help
---

### Post by ewan86 on 2009-09-02
I have a western digital USB500GB external hard drive. If it is connected when I switch on the computer it is recognised and a symbol comes up for it on the desktop and in my computer and in media. When I connect when I am already on ubuntu it wont show up in these locations, though the computer does seem to recognise it when I open a terminal

ewan@ubuntu:~$ lsusb
Bus 001 Device 003: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 062a:0000 Creative Labs Optical mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ewan@ubuntu:~$ 

I am running Ubuntu 9.04 dual boot which I installed using wubi. I have searched the forum but I apologise if I have missed it, Any help would be greatly appreciated.

---

### Post by scouser73 on 2009-09-02
I would assume that if you're using the external hard drive on Windows as well as Ubuntu, that you have to safely remove the hardware, boot into ubuntu and the drive should be recognised then.

---

### Post by ewan86 on 2009-09-02
Hi, 

Thanks for the reply. I have safely removed it in windows, I mainly use ubuntu but I don't always use the external hard drive so I don't plug it in as I don't want to waste power, but when I do plug it in in ubuntu when I am already logged in it's not recognised!! Very frustrating. It doesn't have any problems with pen drives thoug :-s

---

### Post by sedawk on 2009-09-02
Start your computer (and Ubuntu) without the external drive connected.

Clear the message buffer
```

sudo dmesg -c

```

Connect the drive, wait 15 seconds, and post the
new information that is now found in the message buffer:
```

dmesg >dmesg.out

```

(It should say if found a new drive like "sdb", tell something
 about the size and list the partitions on that drive sdb1,sdb2, ...
 If the system has detected the drive but no partitions are mounted
 in /media you can also send the output of "sudo fdisk -l /dev/sdX")

---

### Post by scouser73 on 2009-09-02
I hope that this is of some use to you: [[COLOR="Red"]**Mount Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/")

---

### Post by ewan86 on 2009-09-02
Thanks for the quick replies :o

I followed your instructions and it gave no output after I connected the hard drive, so I assume that means it doesn't recognise it or I did it wrong :-s ??? The first command gave a huge list so I have just copied the last bit

[   35.696144] [drm] Num pipes: 1
[   35.696151] [drm] writeback test succeeded in 1 usecs
[   38.488070] eth0: link down
[   38.488188] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.489439] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   53.545990] ndiswrapper (iw_set_freq:325): setting configuration failed (C0010015)
[   55.684333] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   66.096009] wlan0: no IPv6 routers present
ewan@ubuntu:~$ dmesg >dmesg.out
ewan@ubuntu:~$ 


cheers for help :)

---

### Post by ewan86 on 2009-09-02
after I ran dmesg >dmesg.out I was ran sudo dsmeg -c again out of curiosity and it gave me this output talking about usb so I don't know if thats any use? Also got me thinking that when I use my printer..it's all configured correctly and I have used it but It's only recognised when switched on and plugged in at boot up, maybe it's something to do with the wubi install??

ewan@ubuntu:~$ sudo dmesg -c
[  273.496235] hub 3-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[  273.496245] usb 3-1: USB disconnect, address 2
[  273.804021] usb 3-1: new low speed USB device using ohci_hcd and address 3
[  274.005312] usb 3-1: configuration #1 chosen from 1 choice
[  274.013597] input: HID 062a:0000 as /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input9
[  274.033246] generic-usb 0003:062A:0000.0002: input,hidraw0: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:13.1-1/input0
[  282.656022] usb 1-1: new high speed USB device using ehci_hcd and address 3
[  282.789722] usb 1-1: configuration #1 chosen from 1 choice
ewan@ubuntu:~$

---

