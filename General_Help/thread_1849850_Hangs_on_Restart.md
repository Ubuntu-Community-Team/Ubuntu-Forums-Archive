---
title: "Hangs on Restart"
date: 2011-09-25
forum: General Help
---

### Post by delrin298 on 2011-09-25
I have been messing around trying to figure this out for a while now. I have been using [http://www.brighthub.com/computing/linux/articles/39504.aspx#secn_2](http://www.brighthub.com/computing/linux/articles/39504.aspx#secn_2)
to try and troubleshoot but no luck. 

When i do a verbose restart 
(sudo shutdown "acpi=off" now -r --verbose)
I get all [OK] all the way down and the with the following 2 lines right before the hang.

*Will now restart [OK]
[103.754107] Restarting system.

Then nothing. 

1. Any one have any ideas 
2. Am i passing the ACPI=Off to the shutdown command correctly?

-------------------------------------------
Here is a Little Context for you:
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty

Hardware: Dell Dimension E520 4 Gig RAM
~$ hwinfo --short
> hal.1: read hal dataprocess 3256: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
cpu:                                                            
                       Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz, 2125 MHz
                       Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz, 2125 MHz
keyboard:
  /dev/input/event2    Tangtop USBPS2
mouse:
  /dev/input/mice      Tangtop USBPS2
  /dev/input/mice      Colorado USB Mouse
monitor:
                       Generic Monitor
graphics card:
                       nVidia GeForce 7300 LE
sound:
                       Intel 82801H (ICH8 Family) HD Audio Controller
storage:
                       Floppy disk controller
                       Intel 82801 SATA RAID Controller
network:
  eth0                 Intel 82562V 10/100 Network Connection
network interface:
  lo                   Loopback network interface
  eth0                 Ethernet network interface
  vboxnet0             Ethernet network interface
disk:
  /dev/sda             Hitachi HDS72161
  /dev/sdb             Hitachi HDS72161
  /dev/sdc             ST340062 0AS
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda5            Partition
  /dev/sda6            Partition
  /dev/sda7            Partition
  /dev/sda8            Partition
  /dev/sdb1            Partition
  /dev/sdb2            Partition
  /dev/sdb3            Partition
  /dev/sdc1            Partition
cdrom:
  /dev/sr0             TSSTcorp DVD+-RW TS-H653A
usb controller:
                       Intel 82801H (ICH8 Family) USB UHCI Controller #4
                       Intel 82801H (ICH8 Family) USB UHCI Controller #5
                       Intel 82801H (ICH8 Family) USB2 EHCI Controller #2
                       Intel 82801H (ICH8 Family) USB UHCI Controller #1
                       Intel 82801H (ICH8 Family) USB UHCI Controller #2
                       Intel 82801H (ICH8 Family) USB UHCI Controller #3
                       Intel 82801H (ICH8 Family) USB2 EHCI Controller #1
bios:
                       BIOS
bridge:
                       Intel 82P965/G965 Memory Controller Hub
                       Intel 82P965/G965 PCI Express Root Port
                       Intel 82801H (ICH8 Family) PCI Express Port 1
                       Intel 82801 PCI Bridge
                       Intel 82801HH (ICH8DH) LPC Interface Controller
hub:
                       Linux 2.6.38-11-generic-pae ehci_hcd EHCI Host Controller
                       Linux 2.6.38-11-generic-pae ehci_hcd EHCI Host Controller
                       Linux 2.6.38-11-generic-pae uhci_hcd UHCI Host Controller
                       Linux 2.6.38-11-generic-pae uhci_hcd UHCI Host Controller
                       Linux 2.6.38-11-generic-pae uhci_hcd UHCI Host Controller
                       Linux 2.6.38-11-generic-pae uhci_hcd UHCI Host Controller
                       Linux 2.6.38-11-generic-pae uhci_hcd UHCI Host Controller
memory:
                       Main Memory
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       Intel 82801H (ICH8 Family) SMBus Controller
                       Conexant Dimension 3000
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
  /dev/input/event13   Microsoft® LifeCam Cinema(TM)

---

### Post by delrin298 on 2011-09-25
Not sure if this helps or not, but shutdown works perfectly fine, is only when attempting a restart that the system hangs and after watching several dozen iterations of the shutdown it seems like when the system would power off for a shutdown it is sitting there waiting for something to happen during a restart.

thx,

Delrin

---

