---
title: "Installing drivers for AWUS036H on Ubuntu 10.10"
date: 2011-01-12
forum: General Help
---

### Post by smille89 on 2011-01-12
I am a little new to the internals of the linux system.  I have been using Linux for over a month and have gone through several books on it.  My weak point in linux is system internals and the kernel, (which I am reading up on now).  I am a computer scientist and so I am computer savvy, but have not had much experience until recently with linux.   (I was a windows guy, but Ubuntu 10.10 has changed my opinion)
I am trying to install drivers for the alfa networks wireless adapter AWUS036H.  I followed their online manual and I didn't get very far.  After looking at the error messages then I assume it is a kernel issue.  Here is the error messages I get when I am trying to make the program:

steven@steven-Satellite-A100:~/Downloads/Software/Wireless_Adapters/AWUS051NH/Drivers/RT2870_LinuxSTA_V2.3.0.0$ sudo make
[sudo] password for steven: 
make -C tools
make[1]: Entering directory `/home/steven/Downloads/Software/Wireless_Adapters/AWUS051NH/Drivers/RT2870_LinuxSTA_V2.3.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/steven/Downloads/Software/Wireless_Adapters/AWUS051NH/Drivers/RT2870_LinuxSTA_V2.3.0.0/tools'
/home/steven/Downloads/Software/Wireless_Adapters/AWUS051NH/Drivers/RT2870_LinuxSTA_V2.3.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/steven/Downloads/Software/Wireless_Adapters/AWUS051NH/Drivers/RT2870_LinuxSTA_V2.3.0.0/os/linux/Makefile
make -C /lib/modules/2.6.35-24-generic/build SUBDIRS=/home/steven/Downloads/Software/Wireless_Adapters/AWUS051NH/Drivers/RT2870_LinuxSTA_V2.3.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
  CC [M]  /home/steven/Downloads/Software/Wireless_Adapters/AWUS051NH/Drivers/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/cmm_mac_usb.o
/home/steven/Downloads/Software/Wireless_Adapters/AWUS051NH/Drivers/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitRecv’:
/home/steven/Downloads/Software/Wireless_Adapters/AWUS051NH/Drivers/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/cmm_mac_usb.c:83: error: implicit declaration of function ‘usb_buffer_alloc’
/home/steven/Downloads/Software/Wireless_Adapters/AWUS051NH/Drivers/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/cmm_mac_usb.c:83: warning: assignment makes pointer from integer without a cast
/home/steven/Downloads/Software/Wireless_Adapters/AWUS051NH/Drivers/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/cmm_mac_usb.c:112: error: implicit declaration of function ‘usb_buffer_free’
make[2]: *** [/home/steven/Downloads/Software/Wireless_Adapters/AWUS051NH/Drivers/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/steven/Downloads/Software/Wireless_Adapters/AWUS051NH/Drivers/RT2870_LinuxSTA_V2.3.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make: *** [LINUX] Error 2
steven@steven-Satellite-A100:~/Downloads/Software/Wireless_Adapters/AWUS051NH/Drivers/RT2870_LinuxSTA_V2.3.0.0$ 

I am not sure what is wrong.  I am using Ubuntu 10.10 with 2.6.35-24-generic as the kernel.  With as many people that have gotten it to work then it seems like an easy problem to fix.  If there is anyone that can help me then it would be much appreciated.
Thanks!

---

### Post by Fragel on 2011-02-11
UP!
I have the same error. But my wireless card is AWUS051NH (with chipset rt2870 too).
Anyone can help me?
Thanks!.

---

### Post by Fragel on 2011-02-15
Hi! I found the solution! This solution works properly in my AWUS051NH, but is valid for all wireless card with Ralink 2870 chipset.

Thanks a petermty:

**1.** With adapter connected: fragel@fragel-laptop:~$ lsusb

[I]Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:0900 Logitech, Inc. ClickSmart 310
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 001 Device 002: ID [COLOR="Red"]148f:2070[/COLOR] Ralink Technology, Corp. RT2070 Wireless Adapter**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/I]

**2.** francis@francis-laptop:~$
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "[COLOR="Red"]148f 2070[/COLOR]" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf

[B]¡CARE!: "148f 2070" OK. "148[COLOR="red"]:[/COLOR]2070" ERROR. The "" is correct.
[/B]
**3.** sudo modprobe -rf rt2870sta

sudo modprobe rt2870sta

dmesg | egrep 'rt28|usb|Phy'

**4.** Connect the adapter and check with iwconfig:

[I]lo no wireless extensions.

eth0 no wireless extensions.

wlan0 Ralink STA ESSID:"francis" Nickname:"RT2870STA"
Mode:Managed Frequency=2.437 GHz Access Point:00:18:E7:60:7C:96
Bit Rate=54 Mb/s
RTS thr:off Fragment thr:off
Link Quality=100/100 Signal level:-49 dBm Noise level:-83 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0[/I]

Enjoy! :).

Credits for **petermty** (in Spanish): [http://www.ubuntumexico.org/node/637](http://www.ubuntumexico.org/node/637)

---

