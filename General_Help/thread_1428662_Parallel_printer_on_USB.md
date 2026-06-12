---
title: "Parallel printer on USB"
date: 2010-03-13
forum: General Help
---

### Post by teilnehmer on 2010-03-13
Hi, 

I'm trying to set up a Brother HL-1230 (has only a parallel port) on a Mini-PC with only USB using a parallel/usb adapter cable. I'm running Xubuntu 9.10. The machine is [this]("http://ixsoft.de/cgi-bin/web_store.cgi?ref=Products/de/IXTHM230HW.html"). 

I've found other threads ([here]("http://ubuntuforums.org/showthread.php?t=1320742") or [here]("http://ubuntuforums.org/showpost.php?p=8655615&postcount=30")) suggesting to install the printer at **parallel**:/dev/usb/lp0 (instead of **usb**:/dev/usb/lp0). I tried this with CUPS as well as with the Xubuntu GUI method (followed instructions from the other posts), but to no avail, although I HAVE /dev/usb/lp0 (other people failed because they didn't have it). 

My dmesg outputs the following: 
```

[  310.529243] usb 3-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  310.600467] usb[1724]: segfault at bfd8c000 ip 00988ad3 sp bfd89938 error 4 in libc-2.10.1.so[914000+13e000]
[  331.495771] usb 3-1: USB disconnect, address 2
[  331.496073] usblp0: removed
[  334.520157] usb 3-1: new full speed USB device using ohci_hcd and address 4
[  334.729625] usb 3-1: configuration #1 chosen from 1 choice
[  334.744976] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x1A86 pid 0x7584
[  335.835501] usb 3-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  335.872029] usb[1747]: segfault at bf9c1000 ip 005cead3 sp bf9bd998 error 4 in libc-2.10.1.so[55a000+13e000]

```

The segfault is known from a [bug report]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/436495") which is supposedly fixed. Anyway, the Blacklist for CUPS is not even there on my system, so I don't see how the bug could apply to me, although I DO have the segfault in libc-2.10.1.so. 


When I dmesg | grep -i usb later on I get plenty of repetetions of the first line above (interface 0 claimed by usblp while 'usb' sets config #1) so this is what I believe is the main cause. 

Now: I (I'm a mid-noob, though) have the impression the parallel-thingie could work, but somehow this config #1 is in the way. Any insights what that could be, or alternate theories?

Thanks!

Jan
-- 
lsusb: 
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c312 Logitech, Inc. DeLuxe 250 Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 046d:c046 Logitech, Inc. RX1000 Laser Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

lpinfo -v
```

serial serial:/dev/ttyS0?baud=115200
network http
network socket
network smb
network ipp
network beh
network lpd
direct scsi
direct hp
direct hpfax

```
Interesting that a serial entry is there... I once tried installing a serial printer, so that I could change it to parallel later. Maybe this has to go?

---

### Post by teilnehmer on 2010-03-15
It solved itself! After giving up, I half-heartedly tried another print job, **manually specifying the /dev/usblp0 in Abiword's printing Dialog**. 
Suddenly, some auto-configuring took place. 

I now have my printer at usb://Brother/HL-1230%20series, which shows up as 
```
direct usb://Brother/HL-1230%20series
```
in lpinfo -v. 

Seemingly, the parallel trick would not even have been necessary. The printer now runs on USB.

---

### Post by thodges999 on 2010-06-02
> **teilnehmer said:**
> It solved itself! After giving up, I half-heartedly tried another print job, **manually specifying the /dev/usblp0 in Abiword's printing Dialog**. 
Suddenly, some auto-configuring took place. 

I now have my printer at usb://Brother/HL-1230%20series, which shows up as 
```
direct usb://Brother/HL-1230%20series
```
in lpinfo -v. 

Seemingly, the parallel trick would not even have been necessary. The printer now runs on USB.

Hi there
I have a working USB/parallel adapter and am trying to help others who are still struggling and your experiences may be helpful if you don't mind.

I am still showing the segfault error you mention but I am printing OK. Now you are also printing OK has your segfault gone or is it still there in dmesg|tail?

Your lsusb entry doesnt show a parallel/usb cable being connected, is that still the case (with the printer connected and turned on).

You mention using Abiwords printing Dialog to manually enter the printers address, but I cant find any place to manually enter it only select existng or print to file. Can you advise?

What connector cable do you have as it seems to be better than the Prolific PL2305 I have which even though working doesnt show up with lpinfo -v.

Any help you can give would be appreciated.

---

### Post by teilnehmer on 2010-06-10
Hi!

I'm sorry, but I can't help you with that. I switched to Ubuntu 10.04 and the printer problem didn't occur again (there is a new [bug]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/554172"), though, which I hope will be fixed soon). 

The AbiWord dialog was prompted when I tried to print with no printer set up. AbiWord asked if I wanted to scan for available printers and - tada - there I was. It's too long ago to be more specific, I'm afraid. 

The cable was by Digitus, you can see the one I ordered on [Amazon]("http://www.amazon.de/gp/product/B0002AER84/ref=oss_product"). 

Best of luck! 

Jan

---

