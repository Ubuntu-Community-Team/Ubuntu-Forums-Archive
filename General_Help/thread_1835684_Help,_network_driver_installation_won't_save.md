---
title: "Help, network driver installation won't save"
date: 2011-08-29
forum: General Help
---

### Post by dummyvin on 2011-08-29
Ok, so I'm trying to install the proper driver for my network device, I have the realtek 8111E on my motherboard. This device uses the r8168 driver and Ubuntu carries the r8169. With the r8169 driver my internet speeds suck, and with the r8168 drivers they're perfect.  I've been able to install the driver's and tried to blacklist the r8169 driver but when I restart, the r8169 is still being recognized and it fails to connect to the internet.  If I restart and boot into windows first then restart into Ubuntu the r8169 drivers load :/

```

vinnx@AZUURA:~$ lsmod | grep r8169
r8169                  48022  0 
vinnx@AZUURA:~$ sudo rmmod r8169
vinnx@AZUURA:~$ cd r8168-8.024.00
vinnx@AZUURA:~/r8168-8.024.00$ sudo ./autorun.sh

Check old driver and unload it.
Build the module and install
[: 48: r8168: unexpected operator
Depending module. Please wait.
load module r8168
Completed.
vinnx@AZUURA:~/r8168-8.024.00$ lsmod | grep r8168
r8168                 194904  0 
vinnx@AZUURA:~/r8168-8.024.00$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:d9:2f:5f  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e6f:65ff:fed9:2f5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2297 (2.2 KB)  TX bytes:9335 (9.3 KB)
          Interrupt:41 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

#install goes well, new driver is working perfectly fine. 

``````

vinnx@AZUURA:~/r8168-8.024.00$ sudo gedit /etc/modprobe.d/blacklist.conf

#it opens a txt file with all the blacklisted drivers I think.

(gedit:2162): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.OJ640V': No such file or directory

(gedit:2162): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

# I input 
##blacklist driver r8169
#blacklist r8169

#at the very bottom of page, save file, and I get the msg below.

(gedit:2162): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.7A520V': No such file or directory

(gedit:2162): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2162): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.XSSM0V': No such file or directory

#then when I close the document I get this message below

(gedit:2162): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
vinnx@AZUURA:~/r8168-8.024.00$  #blacklist r8169 driver
vinnx@AZUURA:~/r8168-8.024.00$     blacklist r8169
blacklist: command not found
vinnx@AZUURA:~/r8168-8.024.00$ blacklist r8169
blacklist: command not found
vinnx@AZUURA:~/r8168-8.024.00$
``````

vinnx@AZUURA:~$ lsmod | grep r8169
r8169                  48022  0 
vinnx@AZUURA:~$ 
#restart computer and r8169 driver is loaded and it's not connecting to the internet when it usually does. 

```

---

