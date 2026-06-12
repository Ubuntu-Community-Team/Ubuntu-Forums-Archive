---
title: "How to get IR Remote working with TVTime"
date: 2011-04-11
forum: General Help
---

### Post by satish_j on 2011-04-11
Any ideas how to get the IR Remote working with TvTime application.
I have installed lirc package from synaptic,but dont know how to configure it.
IR sensor is connected to TV Card(in PCI slot).Does this needs to be detected first by Ubuntu.if yes,waht command to use to verify its detection??
The remote came with the TV Card(Philips saa7130 chipset)

---

### Post by tigerstripedcat on 2011-04-11
Did you see this:

[https://help.ubuntu.com/community/InstallLirc/Hardy](https://help.ubuntu.com/community/InstallLirc/Hardy)

A bit old, but it might be a good place to start.

---

### Post by satish_j on 2011-04-11
i tried that link,but i assume it is for hardy as i do not get the screen 'configuring lirc' after installing lirc package.
I use 'sudo dpkg-reconfigure lirc',but that does not list any card with name philips or saa7130.I select a random prolink(card=42).It comes out of configuration w/o any errors.But still,remote is not working.On remote,it is written H-338

---

### Post by satish_j on 2011-04-12
friends,i just found this link which shares a patch for ENABLING H-338 remote
[http://marc.info/?l=linux-video&m=111048935527205&w=2](http://marc.info/?l=linux-video&m=111048935527205&w=2)
But,i cannot figure out how to apply this patch.Can anyone help me out with the patch??
Also,when i run cat /proc/bus/input/devices, this is what I get with:
```

cat /proc/bus/input/devices

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input2
U: Uniq=
H: Handlers=mouse0 event2 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=062a Product=0201 Version=0110
N: Name="USB-compliant keyboard"
P: Phys=usb-0000:00:13.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=120013
B: KEY=1000000000007 ff9f207ac14057ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=062a Product=0201 Version=0110
N: Name="USB-compliant keyboard"
P: Phys=usb-0000:00:13.0-1/input1
S: Sysfs=/devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.1/input/input4
U: Uniq=
H: Handlers=kbd mouse1 event4 
B: EV=1f
B: KEY=fe00000 0 0 877fff002c3027 bf00444400000000 1 c040a27c000 267bfad941dfed 9e000000000000 0
B: REL=143
B: ABS=100000000
B: MSC=10

I: Bus=0003 Vendor=15d9 Product=0a4c Version=0111
N: Name=" USB OPTICAL MOUSE"
P: Phys=usb-0000:00:13.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.0/input/input5
U: Uniq=
H: Handlers=mouse2 event5 
B: EV=17
B: KEY=70000 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0001 Vendor=10ec Product=0885 Version=0001
N: Name="HDA Digital PCBeep"
P: Phys=card0/codec#0/beep0
S: Sysfs=/devices/pci0000:00/0000:00:14.2/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=40001
B: SND=6

```

---

### Post by satish_j on 2011-04-13
okay,atleast can anyone tell me what does the command 'cat /proc/bus/input/devices' do??

---

### Post by satish_j on 2011-04-20
bump..
:(

---

### Post by satish_j on 2011-04-21
tried using mode2,but it gives foll:also,dmesg shows driver for IR loaded
```

sudo mode2 -d /dev/lirc0
[sudo] password for satish:           
mode2: could not get file information for /dev/lirc0
mode2: default_init(): No such file or directory
satish@Titan:~$ dmesg | grep lirc
[   22.756038] lirc_dev: IR Remote Control driver registered, major 61 

```
any ideas now..
ANYONE!!!!!!!!!11

---

### Post by satish_j on 2011-04-29
iam still looking for a solution:
Just found that hardware.conf file lists the file /dev/lirc0,whereas the file does not actually exist.
If i run 'sudo modprobe lirc_serial', file(/dev/lirc0) gets created,but mode2 still gives the error.

---

### Post by satish_j on 2011-05-16
A regrettable bump...
Is there no-one using IR Blaster with TVtuner?

---

### Post by satish_j on 2011-07-04
iam using this IR receiver which plugs directly into the Tuner card.
Does Linux has support for such IR devices?
Iam asking this as there is no mention of IR detection in output of cat /proc/bus/input/devices??
any suggestion greatly appreciated...

---

### Post by satish_j on 2011-07-15
friends,i just came to know that there is no support yet for IR devices that plug into the TV tuner card, in Linux.
Iam now planning to purchase a USB IR blaster.
Just wanted to know whether it will work or not??
I mean, TV tuner card is into one of the pci slots,while ir device will go into one of the USB slots.
Will this combination work?
Pls suggest..

---

### Post by satish_j on 2011-07-16
no one!!!:(

---

