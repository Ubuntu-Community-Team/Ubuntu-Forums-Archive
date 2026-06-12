---
title: "lirc + jetway nvidia ion"
date: 2010-12-14
forum: General Help
---

### Post by yeleek on 2010-12-14
Hi,

Trying to get the IR working on a new jetway nvidia mini-itx ion.  Have installed lirc, but I'm not sure the receiver is actually being detected...

cat /proc/bus/input/devices 
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0003 Vendor=1241 Product=f767 Version=0110
N: Name="HOLTEK Wireless 2.4GHz Trackball Keyboard"
P: Phys=usb-0000:00:06.0-3/input0
S: Sysfs=/devices/pci0000:00/0000:00:06.0/usb4/4-3/4-3:1.0/input/input2
U: Uniq=
H: Handlers=sysrq kbd event2 
B: EV=120013
B: KEY=10000 7 ff9f207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=1241 Product=f767 Version=0110
N: Name="HOLTEK Wireless 2.4GHz Trackball Keyboard"
P: Phys=usb-0000:00:06.0-3/input1
S: Sysfs=/devices/pci0000:00/0000:00:06.0/usb4/4-3/4-3:1.1/input/input3
U: Uniq=
H: Handlers=kbd mouse0 event3 
B: EV=1f
B: KEY=837fff 2c3027 bf004444 0 0 70001 f84 8b27c000 667bfa d941dfed 9e0000 0 0 0
B: REL=143
B: ABS=1 0
B: MSC=10

The remote is a no name generic type thing, but surely the first part is to get the receiver detected, can anyone help pls?

Thanks

---

### Post by yeleek on 2010-12-15
In case anyone has same problem.  Found this, tried it (using 10.10 drivers) and remote is now working fine in XBMC/Ubuntu.

[http://forums.boxee.tv/showthread.php?t=17684](http://forums.boxee.tv/showthread.php?t=17684)

---

### Post by james_xxx on 2010-12-16
Could I ask what Jetway machine you bought?

I purchased a Jetway Mini-TOP HBJC600C99-52W-BW 6-8 weeks ago.

I really like this little machine a lot, and would love to get the remote functioning more fully.

Thanks!

---

### Post by yeleek on 2010-12-17
I bought this one:

[http://linitx.com/viewproduct.php?prodid=12705](http://linitx.com/viewproduct.php?prodid=12705)

HTH

Found this - worth a look - does mention IR.
[http://forum.xbmc.org/showthread.php?t=78722](http://forum.xbmc.org/showthread.php?t=78722)

---

### Post by bedege on 2011-02-10
Hi there

I actually purchased a similar Jetway Ion-Top HTPC. Main difference with Yeleek's is that it's more recent, based on Atom D525 + Ion2 GPU. Its exact reference is [JBC231C98-525]("http://www.jetwaycomputer.com/ITX-JBC231C98-525.html"), and is available from Newegg or LinITX.

Since this newer machine's case is looking identical to Yeleek's, I was wondering if it actually has the same Nuvoton builtin IR receiver, and thus could work using nct677x lirc modules from Asrock, as explained in several threads on Ubuntuforums.org?

Does anybody have any clue? Any way to figure that out with Ubuntu, without actually installing the Nuvoton driver and giving a try? I don't have any M$ OS on that HTPC, and no plan to do so :P

Thanks

---

### Post by bedege on 2011-02-11
After looking at (way too many) other threads on lirc/remote/jetway, I noticed that Jetway's other HTPC, ie mini-top (JBC600C99352W) that shares many common features with my ion-top (JBC231C98-525), namely Atom D525 and Ion2 GPU,  apparently uses a different CIR system.

Could someone explain how I could check if my own system has a Nuvoton IR system (like older ion-top) or a more recent system that works with Aureal HID driver? I don't have M$ windows on my box, so I'm only relying on Ubuntu to make the remote work :D

Thanks

---

