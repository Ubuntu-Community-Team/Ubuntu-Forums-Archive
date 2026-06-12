---
title: "Install on USB 2.0 slow"
date: 2010-09-16
forum: General Help
---

### Post by nuevounix on 2010-09-16
I install Ubuntu 9.10 on USB 8GB with out problem and work good but is slow I'm been researching the cause but I can not find out what is the problem why is so slow these are my spects:

pentium 4
1GB memory 
50: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7_if0
  Unique ID: k4bc.9T1GDCLyFd9
  Parent ID: 5YuN.pOajoWc6Gh4
  SysFS ID: /devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0
  SysFS BusID: 1-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.31-22-generic ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.31-22-generic ehci_hcd"
  Device: usb 0x0002 "EHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:1d.7"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #23 (USB Controller)

USB speed looks ok I guess ?

This how I installed it:
1. Unplug HD
2. CD installation  and select UBS flash drive no problems.
Is this the rigth way to do the installation? 

Every thing works ok but very slow?

Any help will be welcome.!

---

### Post by Mark Phelps on 2010-09-16
I don't know how "slow" it is, but it's going to be slower than a hard disk installation if, for no other reason, than you have to go through the USB port every time you want to do anything.

Perhaps others who have installed to USB can offer you their experience on expected performance of USB vs. HDD.

---

