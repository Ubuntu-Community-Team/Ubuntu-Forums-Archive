---
title: "Lucid Lost DSL Connection"
date: 2010-09-13
forum: General Help
---

### Post by th1bill on 2010-09-13
The computer is a K9n6pgm2+ mainboard w/2gig of RAM and an AMD Phenom Triple Core. My Harddrives are /dev/sda=320gig and /dev/sdb=80gig. Resident on sda is Ubuntu 10.04 (fresh install) w/Windows XP installed at the final 40 gigs, installed after Ubuntu install and then used the 9.10 live CD to reinstall GRUB. On /dev/sdb is Ubuntu 9.10.

I installed the fresh Lucid install 3 months ago when I purchased the 320 gig HDD to replace the failing 40 gig and it has run perfectly until yesterday. I presently have a 2Wire Modem located at 172.16.0.1 and I have a new Motorola in the mail but I presently cannot get Lucid to find my internet connection.

If I boot into XP everything is fine. i can go all over the net. If I boot into Karmic, all is well. I am typing this in Karmic so it is strictly a Lucid problem and I have tried all that I know to do and I really want my Lucid install back...Help?

---

### Post by MooPi on 2010-09-13
Can you use this command and post the results ?
```
ifconfig -a
```

---

### Post by th1bill on 2010-09-13
> **MooPi said:**
> Can you use this command and post the results ?
```
ifconfig -a
```
Thank you for your help, the read out is below.

th1bill@th1bill-desktop:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 40:61:86:06:5a:82  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2328 (2.3 KB) 
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:204 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:204 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:19512 (19.5 KB)  TX bytes:19512 (19.5 KB) 

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

th1bill@th1bill-desktop:~$

---

### Post by MooPi on 2010-09-13
Go to /etc/network/interfaces and see if your eth0 is listed. This is what mine looks like.


```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

---

### Post by th1bill on 2010-09-13
> **MooPi said:**
> Go to /etc/network/interfaces and see if your eth0 is listed. This is what mine looks like.


```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

No, mine reads:
> auto lo
iface lo inet loopback

---

### Post by MooPi on 2010-09-13
Well add the appropriate lines  for eth0 and add for good measure ```
ifup eth0 
```You may need a reboot to set this or log out then in ,not certain. You do use dhcp to connect ? Or are you using a static address ?

---

### Post by th1bill on 2010-09-13
> **MooPi said:**
> Well add the appropriate lines  for eth0 and add for good measure ```
ifconfig eth0 up
```
You may need a reboot to set this or log out then in ,not certain. You do use dhcp to connect ? Or are you using a static address ?

I'll try this and I use dhcp.

---

### Post by th1bill on 2010-09-14
I copied your list and then after saving it I rebooted into Lucid.  I went to the /sdb drive and opened the file and copied it once more.  I then opened my copy of it and replaced it with yours.  I rebooted once more and I am now typing from my Lucid install.

Thank you very much and if you are ever in SE Texas let me know and we'll have some coffee.

---

### Post by GalgoLance on 2010-09-23
I'm a newbie at Ubuntu, but this might help others who are not very adept at Linux as of yet:
Experienced Linux persons probably don't need this explanation, but new persons might.

In Lucid Lynx, the file you need to access and modify as shown above is owned by "root". 
Perhaps this way with other versions, I don't know.

So, if you just open Gedit and try to edit the file, it won't work, as the file is Read Only.

To get around this, you must issue commands as Root or Super User.

To do that, go to Applications and open the Terminal window.

In the Terminal window, type:

sudo gedit /etc/network/interfaces

your computer will ask for the Root password.  If you don't know it, you are out of luck.

Anyway, if you get this far, the screen will show that you do Not have an "auto eth0" which is your wired internet connection.  Just like th1Bill and Moopi say above. 

Edit the file as MooPi says above by copying and pasting this in place of whatever you see or by adding the missing lines.  

# This file describes the network interfaces available on your system 
# and how to activate them. For more information, see interfaces(5).  
# The loopback network interface 

auto lo 
iface lo inet loopback 
 

# The primary network interface 

auto eth0 
iface eth0 inet dhcp



OK.  If all is well, just save the file in Gedit and you are done with that.

Now you need to restart the Network in order to make the changes effective.

Reboot the system is one way.

Another is to use your Terminal Window and issue this command:

sudo /etc/init.d/networking restart

This will force the system to restart  your network connections and recognize auto etho. 
That should do it.  I have no idea why the interface file got messed up, but it happened when I allowed Update Manager to install some stuff.  

Good Luck.

---

