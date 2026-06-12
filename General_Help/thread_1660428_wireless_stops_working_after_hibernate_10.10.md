---
title: "wireless stops working after hibernate 10.10"
date: 2011-01-05
forum: General Help
---

### Post by PetePete on 2011-01-05
says wireless unavaliable, do a ifconfig and it doesn't show up.

need to restart computer to get wireless back.

any way I can fix this?
or even a command to run to restart the wireless
(/etc/init.d/networking restart doesn't work)

wireless chip: RT2500

cheers

---

### Post by TBABill on 2011-01-05
How long have you waited after it coming back from hibernate? Mine won't work for 30 sec to 1 min after opening my laptop from suspend but it eventually does connect. Until it connects it shows no available networks and acts like there is no driver, but shortly after that it starts working again. No known reason why that I have found yet.

---

### Post by PetePete on 2011-01-05
i went and made a coffee, came back and it still wasn't working :(

i ended up pluggin in my phone and that worked for usb tethering until i got round to rebooting!

---

### Post by Mark Phelps on 2011-01-06
If your wireless is a USB device, you're probably out of luck.  I had to give up using Ubuntu on a laptop because I was using USB-connected keyboard and mouse, and after every hibernate, the USB devices were no longer recognized.  I had to reboot cold to get them back.

If it's an internal device, can't help you there. Sorry.  You might have better luck posting this in the Networking subforum.

---

### Post by lrgmmc on 2011-01-06
it might help to know what laptop you are using. there are different hibrinate scripts for some.

---

### Post by PetePete on 2011-01-06
its built in wireless for my laptop which isn't a well known make.

$lshw

description: Notebook
    product: MS-1011
    vendor: MICRO-STAR INT'L CO.,LTD.
    version: 0101
    serial: FFFFFFFF
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.1 smp
    configuration: chassis=notebook cpus=1 
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: A1011SE5 V1.50 09/08/05 (09/08/2005)

---

### Post by MaxIBoy on 2011-01-06
Try 
```
sudo service networking restart
sudo service network-manager restart
```

Ubuntu now uses upstart instead of system V init, so the commands to restart some services are different now.

---

### Post by lrgmmc on 2011-01-06
can you post
```
lspci -nn | grep Network
lsmod | grep rt2
```

---

### Post by PetePete on 2011-01-06
```

pete@laptop:~$ sudo lspci -nn | grep Network
[sudo] password for pete: 
00:0e.0 Network controller [0280]: RaLink RT2500 802.11g [1814:0201] (rev 01)

```

```

pete@laptop:~$ sudo lsmod | grep rt2
rt2500pci              13731  0 
rt2x00pci               6029  1 rt2500pci
rt2x00lib              27275  2 rt2500pci,rt2x00pci
led_class               2633  1 rt2x00lib
mac80211              231541  2 rt2x00pci,rt2x00lib
cfg80211              144470  2 rt2x00lib,mac80211
eeprom_93cx6            1345  1 rt2500pci

```

---

### Post by lrgmmc on 2011-01-06
yoou should try this.
before hibernating run```
modprobe -r rt2500pci
```
then when you resume run```
modprobe rt2500pci
```
see if that works.

---

### Post by PetePete on 2011-01-07
thanks that works.
Could you (or someone) tell me which scripts I can put that in so that it happens on hibernate shutdown, and hibernate startup ?

ta

---

### Post by lrgmmc on 2011-01-07
from this post [http://ubuntuforums.org/showpost.php?p=8977984&postcount=2](http://ubuntuforums.org/showpost.php?p=8977984&postcount=2)
Create a new file named 0000wireless in /usr/lib/pm-utils/sleep.d


```
sudo nano /usr/lib/pm-utils/sleep.d/0000wireless
``` and add
```

#!/bin/sh

# reload wireless

case "$1" in
        resume|thaw)
                modprobe -r rt2500pci
                modprobe rt2500pci
                ;;
esac

```then make it executable.
```
chmod a+x /usr/lib/pm-utils/sleep.d/0000wireless
```

---

