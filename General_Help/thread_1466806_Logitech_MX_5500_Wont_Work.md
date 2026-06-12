---
title: "Logitech MX 5500 Wont Work"
date: 2010-04-30
forum: General Help
---

### Post by Technique13 on 2010-04-30
Hi All,

Cannot for the life of me get my MX 5500 logitech keyboard/mouse combo to work with 10.04. It worked with 9.10 and 9.04 fine out of the box, but i upgraded my computer to the new version and suddenly it wont work at all. I have tried pairing it with the bluetooth manager to no avail. Did some research and i believe the problem is it wont switch over to CVS mode or something which would let it also work in the bios.

Can anyone help me? or has anyone else got the MX 5500 set and has it working?

Cheers,
T

---

### Post by Technique13 on 2010-04-30
found a solution for anyone who has this problem:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/444420](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/444420)

---

### Post by rz2k on 2010-05-01
same for me, cant get mx5500 working even with udev rules from launchpad link above.

---

### Post by Nigel Pegram on 2010-05-03
I can confirm this bug. Immediately on upgrade to Lucid, my MX 5500 ceased to work (both keyboard and mouse). The hardware is fine--works on Windows 7 machine.

I looked at /lib/udev/rules.d/70-hid2hci.rules and the abovementioned fix seems to have been incorporated. The adapter seems to be recognised  and in HCI mode, as the following lines from lsusb shows:

Bus 003 Device 028: ID 046d:c709 Logitech, Inc. BT Mini-Receiver (HCI mode)
Bus 003 Device 027: ID 046d:c71c Logitech, Inc. 
Bus 003 Device 026: ID 046d:c71b Logitech, Inc. 
Bus 003 Device 025: ID 046d:0b06 Logitech, Inc.

---

### Post by efflandt on 2010-05-03
The bug 444420 solution is what actually broke it for most of us.  I started researching this after someone mentioned that their Logitech diNovo keyboard failed to work in 10.04.  I thought that was really strange when it seems to be totally OS independent (it works for my BIOS password before any OS boots).  So I tried a 10.04 LTS live CD and my diNovo Edge did not work.

I did stumble on bug 444420, but that has a solution of changing hidraw* (which worked for me in 9.10) to hiddev* (which does not work for me, and is the default for 10.04).

So one solution is to change hiddev* back to hidraw* in /lib/udev/rules.d/70-hid2hci.rules.  But maybe Linux does not need even need to pay attention to it at all, because  another solution is to simply comment out that section as follows.

```
# Logitech devices
#KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
#  RUN+="hid2hci --method=logitech-hid --devpath=%p"
```Unplug your USB wireless keyboard dongle, and plug it back in, then see if your keyboard and mouse (or mousepad) work.  That worked for me.

---

### Post by VioletCrime on 2010-05-16
> **efflandt said:**
> The bug 444420 solution is what actually broke it for most of us.  I started researching this after someone mentioned that their Logitech diNovo keyboard failed to work in 10.04.  I thought that was really strange when it seems to be totally OS independent (it works for my BIOS password before any OS boots).  So I tried a 10.04 LTS live CD and my diNovo Edge did not work.

I did stumble on bug 444420, but that has a solution of changing hidraw* (which worked for me in 9.10) to hiddev* (which does not work for me, and is the default for 10.04).

So one solution is to change hiddev* back to hidraw* in /lib/udev/rules.d/70-hid2hci.rules.  But maybe Linux does not need even need to pay attention to it at all, because  another solution is to simply comment out that section as follows.

```
# Logitech devices
#KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
#  RUN+="hid2hci --method=logitech-hid --devpath=%p"
```Unplug your USB wireless keyboard dongle, and plug it back in, then see if your keyboard and mouse (or mousepad) work.  That worked for me.


Worked like a charm; thanks a bunch! ^_^ b

---

### Post by kharntiitar on 2010-05-24
> **efflandt said:**
> The bug 444420 solution is what actually broke it for most of us.  I started researching this after someone mentioned that their Logitech diNovo keyboard failed to work in 10.04.  I thought that was really strange when it seems to be totally OS independent (it works for my BIOS password before any OS boots).  So I tried a 10.04 LTS live CD and my diNovo Edge did not work.

I did stumble on bug 444420, but that has a solution of changing hidraw* (which worked for me in 9.10) to hiddev* (which does not work for me, and is the default for 10.04).

So one solution is to change hiddev* back to hidraw* in /lib/udev/rules.d/70-hid2hci.rules.  But maybe Linux does not need even need to pay attention to it at all, because  another solution is to simply comment out that section as follows.

```
# Logitech devices
#KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
#  RUN+="hid2hci --method=logitech-hid --devpath=%p"
```Unplug your USB wireless keyboard dongle, and plug it back in, then see if your keyboard and mouse (or mousepad) work.  That worked for me.

worked a treat for me aswell .. thanks heaps!!!!!

---

### Post by Roanoke on 2010-06-19
This has worked for me as well, it seems. I've been trying to get this working for a loong time, it's nice to see that it finally works.

No idea why those lines were added (for the sake of adding, perhaps?)

---

### Post by brendanmc on 2010-06-29
The fact that the MX5500 uses bluetooth got me thinking.... so I am presuming that although the devices work through the BIOS, once linux boots the USB stick is recognised as a bluetooth adapter and control of it is passed from the BIOS to the kernel driver. 

Ubuntu then just treats it like a standard bluetooth adapter, trouble being that as yet it has no paired devices according to the driver. 

FIX: I plugged in another keyboard and mouse temporarily, click the bluetooth symbol in the gnome panel, selected preferences, Clicked on "Setup New Device". I then pressed the red connect button under both keyboard and mouse. Both the keyboard and mouse were found. Mouse paired without issue, the ubuntu driver then gave me a passcode for the keyboard and suggested that I enter it and press "Enter". Keyboard screen showed that it wanted me to enter the pass code too :) Worked first go. 

Media control keys on LHS of keyboard work properly. LCD still seems fairly useless. 

Cheers
Brendan

---

### Post by moresun on 2010-09-04
Thanks Efflandt

Changing the /lib/udev/rules.d/70-hid2hci.rules like you posted worked perfect. My MX5500 stopped working after a normal update on 10.04

Greetings

Max

> **efflandt said:**
> 
```
# Logitech devices
#KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
#  RUN+="hid2hci --method=logitech-hid --devpath=%p"
```Unplug your USB wireless keyboard dongle, and plug it back in, then see if your keyboard and mouse (or mousepad) work.  That worked for me.

---

### Post by lukeluke on 2011-10-14
I know this is an old thread but just to say that the solution works also now with the upgrade from 11.04 to 11.10!

Except I had to modified the file /lib/udev/rules.d/62-bluez-hid2hci.rules instead...

I wrote that I found the solution in this thread in this bug report: [https://bugs.launchpad.net/ubuntu/+bug/870227](https://bugs.launchpad.net/ubuntu/+bug/870227)

---

### Post by lukeluke on 2012-01-28
> **lukeluke said:**
> I know this is an old thread but just to say that the solution works also now with the upgrade from 11.04 to 11.10!

Except I had to modified the file /lib/udev/rules.d/62-bluez-hid2hci.rules instead...

I wrote that I found the solution in this thread in this bug report: [https://bugs.launchpad.net/ubuntu/+bug/870227](https://bugs.launchpad.net/ubuntu/+bug/870227)

Had the exact same problem after my upgrade from 11.10 to 12.04. This time the file I had to edit to make my MX5500 to work is /lib/udev/rules.d/97-bluetooth-hid2hci.rules

---

### Post by reality1011 on 2012-03-24
This is still working :)  

I just performed a fresh install of 11.10 and this worked for me.  Required me to perform a grep for "hiddev", returning 3 files.  The Logitech comments were located in : **[COLOR="Red"]62-bluez-hid2hci.rules[/COLOR]**

Thanks!

---

### Post by killernet on 2012-05-17
hashing out the logitech worked for me on 12.04LTS,  big thanks ;)

---

