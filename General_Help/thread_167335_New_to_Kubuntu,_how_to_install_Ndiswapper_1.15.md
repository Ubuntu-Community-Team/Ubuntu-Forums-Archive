---
title: "New to Kubuntu, how to install Ndiswapper 1.15"
date: 2006-04-28
forum: General Help
---

### Post by Flowing_air on 2006-04-28
I just installed kubuntu 5.10 several days ago. I try to install Ndiswapper so that i can use wireless to access to internet.
But the problem is my kernel veision is 2.6.12-9-386, so i have to follow  instruction here:
-------------------------------------------------------------------------------------------------------
You need a recent kernel at least 2.6.6 or 2.4.26 with source. Under Red Hat or Mandrake, the sources can be installed using the package kernel-source< kernel-version >.rpm. Make sure there is a link to the kernel source from the modules directory. /lib/modules/VERSION/build should be a link to the kernel source, where VERSION is the version of the kernel you are running. If there is no link, you'll get an error at the make install step. To create a link, assuming the kernel sources are present, use the command
 
 ln -s /usr/src/linux-< kernel-version > /lib/modules/VERSION/build
-----------------------------------------------------------------------------------------------------------

use the commands:
sudo ln -s/usr/src/linux-<kernel-version> /lib/modules/2.6.12-9-386/build
sudo ln -s/usr/src/linux-<kernel-2.6.12-9-386> /lib/modules/2.6.12-9-386/build
sudo ln -s/usr/src/linux-<2.6.12-9-386> /lib/modules/2.6.12-9-386/build
sudo ln -s/usr/src/linux-2.6.12-9-386 /lib/modules/2.6.12-9-386/build

but none of them works.  It always show that: kernel-version/kernel-2.6.12-9-386/2.6.12-9-389: there is no such file or directory.

any one can help me with this????

---

### Post by gondilon on 2006-04-28
try doing sudo apt-get install ndiswrapper-utils

---

### Post by Flowing_air on 2006-04-28
It is very helpfull. And i have installed 1.1version now.
But it still doesn't work...


brant@CMGY:~$ ndiswrapper -l
Installed ndis drivers:
gplus   driver present, hardware present 

brant@CMGY:~$ sudo depmod -a
brant@CMGY:~$ modprobe ndiwrapper
FATAL: Module ndiwrapper not found.
brant@CMGY:~$ sudo depmod -a
brant@CMGY:~$ sudo modprobe ndiswrapper


brant@CMGY:~$ sudo dmesg
 20
[4294670.204000] ACPI wakeup devices: 
[4294670.204000] C059 C0AB C0B1 C0B4 C184 C17A C17B C193 C137 
.
.
.
Hundreds lines stuff here...
.
.
.
[4294729.188000] [drm] Loading R200 Microcode
[4297031.362000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)

brant@CMGY:~$  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  Nickname:"acx100 v0.2.0pre8"
iwconfig: symbol lookup error: iwconfig: undefined symbol: iw_sawap_ntop

brant@CMGY:~$ more /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp


brant@CMGY:~$ ls /etc/modprobe.d/
aliases    arch-aliases       isapnp
alsa-base  bluez              nvidia-kernel-nkc
arch       ibm_acpi.modprobe  toshiba_acpi.modprobe


And  my wireless card is D-link DWL-G650+

---

### Post by Flowing_air on 2006-04-28
and with this command:
brant@CMGY:~$ kdesu kate /etc/network/interfaces

i got a file:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

---

### Post by Flowing_air on 2006-04-28
Oh, Kubuntu.....Do u know, i love you so much.
And bring me so difficult love to enjoy...](*,) ](*,)

---

### Post by Flowing_air on 2006-04-28
Anyone  please..............

---

### Post by gondilon on 2006-04-29
after you run sudo modprobe nidiswrapper, look in your network connections and see if your wireless card dhows up. ALso, get Kwifimanager if you do not already have it and see if that works.

---

