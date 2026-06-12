---
title: "Stuck on one part when setting up wireless on a ze2000"
date: 2006-05-08
forum: General Help
---

### Post by Silentheero on 2006-05-08
I was searching on this board and google and finally found this site that explains everything step by step [http://doc.gwos.org/index.php/Install_ipw2200](http://doc.gwos.org/index.php/Install_ipw2200) . I followed everything to the letter (using the numbers for the newer versions) but got stuck on Installing ieee80211. 

```

cd ieee80211-1.1.13 
make && sudo make install 
cd ..

```

This is what happens when I do it:
```

/tmp/wifi/ieee80211-1.1.13$ make && sudo make install
/bin/sh: cc: command not found
Checking in /lib/modules/2.6.12-9-386 for ieee80211 components...
make -C /lib/modules/2.6.12-9-386/build M=/tmp/wifi/ieee80211-1.1.13 modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /tmp/wifi/ieee80211-1.1.13/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/tmp/wifi/ieee80211-1.1.13/ieee80211_module.o] Error 127
make[1]: *** [_module_/tmp/wifi/ieee80211-1.1.13] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [modules] Error 2

```

I have installed on a ze2000 ([http://www.hothardware.com/viewarticle.aspx?articleid=651&cid=10](http://www.hothardware.com/viewarticle.aspx?articleid=651&cid=10))
that has 768 RAM now.

Had to apt-get the "make" command. Could that be a problem?
Any ideas?

---

### Post by Silentheero on 2006-05-08
*bump*

---

### Post by Silentheero on 2006-05-08
Ok, I went to the Synaptic Package Manager and got all the following (not sure which ones i needed but i got anyway):

gcc 3.4
cpp
binutils
linux-headers
kernel source code

after installing those, the process continued and I was able to finish the steps.

On the next to the last step though, Putting fw in place when i type:
```
sudo cp * /usr/lib/hotplug/firmware
```
it gives me:
```
cp: omitting directory `ipw2200-fw-3.0'
```
meaning that it won't copy the directory. So i manually put the files inside the directory into the firmware folder. Then the last step, Load the Firmware, gives me nothing when i type:
```
sudo modprobe ipw2200
```

Again, I am following the instructions from [http://doc.gwos.org/index.php/Install_ipw2200]("http://doc.gwos.org/index.php/Install_ipw2200")

Any suggestions?

---

### Post by Silentheero on 2006-05-09
anyone?

---

### Post by Silentheero on 2006-05-09
While waiting and hoping that someone who has been through this before comes along and tells me exactly whats wrong ;) , I have been working with ndiswrapper. I have found the driver for my card by following the instructions on [this]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto") site :

PCI-ID 14e4:4320
Network Controller: Broadcom Corp BCM4306 802.11b/g Wireless LAN Controller (rev 03)

driver bcmwl5.inf

and using the graphical interface (System -> Administration -> Windows Wireless Drivers) installed the driver. Under the "Currently installed Windows Drivers" window is my driver and "Hardware Present: Yes". 

Great news.... except when I do a iwconfig or check out the network settings in System-> Administration-> Networking there is no mention of a WLAN or anything other than:
```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


```

What now?

And if you view this and cant help, at least post so that this hopefully gets bumped to someone who can help. I know someone else with this notebook has had a problem. :)

---

### Post by Silentheero on 2006-05-10
Finally found the problem and corrected it, got WPA working and am online wirelessly. Its late so I will create a howto for this later, for my sanity and others who will run into this problem. 

If nothing else, this was a post for me to gather my thoughts. Hope you all can help me next time. 8)

---

### Post by Silentheero on 2006-05-15
I am working on the wireless and was not had too much of a problem, except for one thing. Every time I start Ubuntu I have to enter 
```
 sudo wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf
sudo dhclient wlan0
```

I have tried editing the /etc/network/interfaces and /etc/default/wpasupplicant files like some of the threads and sites say, but none of them automatically connect to the net. And doing so I believe I have royally nerfed the interfaces file and maybe the supplicant file. Here is what I have ATM:

interfaces:
```
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

# WLAN Home
auto wlan0
iface wlan0 inet static
address 192.168.1.104
netmask 255.255.255.0
gateway 192.168.1.2
        wireless_mode managed
        wireless_channel 6
        post-down pump -k
        wireless-essid linksys
pre-up /etc/init.d/wpasupplicant start
pre-up sleep 5
pre-up wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf
pre-up dhclient wlan0
post-down killall -q wpa_supplicant

iface eth0 inet static
address 192.168.1.104
netmask 255.255.255.0
gateway 192.168.1.2

iface wlan0 inet static
address 192.168.1.104
netmask 255.255.255.0
gateway 192.168.1.2
wireless-essid linksys
wireless-key s:*********

``` 

supplicant:
```
# /etc/default/wpasupplicant

# WARNING! Make sure you have a configuration file!

ENABLED=1

# Useful flags:
#  -D <driver>          Wireless drive, typically optional.
#  -i <ifname>          Interface
#  -c <config file>     Configuration file
#  -d                   Debugging (-dd for more)
#  -w                   Wait for interface to come up

# See the manual page wpa_supplicant(1) for more options and information.

OPTIONS="iwlan0 -c/etc/wpa_supplicant.conf -Dndiswrapper -w"

# EXAMPLES:

# OPTIONS="-i wlan0 -D hostap -c /etc/wpa_supplicant.conf"
# OPTIONS="-i ath0 -D madwifi -c /etc/wpa_supplicant.conf"

```

If someone doesn't mind, could you check to see what I need and what I dont, and how I need to set the wireless to connect automatically? It would be a great help to me. Besides "Beginning Ubuntu Linux" book from Apress and this forum, I dont have anyone to help me with linux. I need to find a hacker (not cracker) friend. :-D

---

### Post by nelsonb73 on 2006-06-20
Looks like you need a -i at the beginning of your options line...

***OPTIONS="[COLOR="Red"]-i [/COLOR]iwlan0 -c/etc/wpa_supplicant.conf -Dndiswrapper -w"***

---

