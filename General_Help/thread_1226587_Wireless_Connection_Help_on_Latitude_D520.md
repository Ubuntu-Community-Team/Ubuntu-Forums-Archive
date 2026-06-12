---
title: "Wireless Connection Help on Latitude D520"
date: 2009-07-29
forum: General Help
---

### Post by bloodlust757 on 2009-07-29
Hey guys im new to ubuntu. Just started running it about 3 days ago.  I didnt have this problem when i was running XP. My wired connection into my router is perfectly fine but when i go wireless ill stay connected for maybe 5 min max and my connection drops.  Thing is ubuntu says im still connected but i cant ping to my router. When i do try to ping to i get "destination host unreachable" not "request timed out" thing is my router is the first hop on my network so what gives? 

I have a WEP key running and my SSID isnt broadcasted but thats not a problem on my other pcs.

and i read some stuff on other sites that i had to download some stuff for my laptop (search for bcm43xx and installed it?) other people said it worked for them but im still having problems

help would be great.

---

### Post by bloodlust757 on 2009-07-30
friendly bump

please help someone

---

### Post by realzippy on 2009-07-30
Maybe you should specify your question.If you found out that you run a bcm 43xx wlan chip e.g.:
connection loss bcm 43xx

titled in Networking & Wireless Category.

---

### Post by realzippy on 2009-07-30
by the way,is your bcm driver enabled in System/Administration/Hardware drivers?

---

### Post by bloodlust757 on 2009-07-31
sorry zippy. ur right

how do i check what im running?
sorry very new to ubuntu like i said before so yea


i did check my drivers 
it says im not using any.....

---

### Post by realzippy on 2009-07-31
If there is  a driver offered,you should install it by checking the button...  (The driver is called bc43 or sort of)...

---

### Post by realzippy on 2009-07-31
[https://lists.ubuntu.com/archives/ubuntu-users/2008-May/145063.html](https://lists.ubuntu.com/archives/ubuntu-users/2008-May/145063.html)

...could also help if there is no driver offered

---

### Post by bloodlust757 on 2009-07-31
ok well i did a "lspci"
and i found that im using a 
 Broadcom Corporation BCM4401-B0 100Base-TX
soooo im gesing the bcm43xx isnt gonna work for me.....
and im trying to follow this guide
[http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper)
but i cant blacklist anything
do i need to create the file called blacklist?

---

### Post by bloodlust757 on 2009-07-31
ok so i was able to black list it
but i cant find the proper driver to use....
my wireless card wasnt on that list.....

---

### Post by atomizer on 2009-07-31
Broadcom Corporation BCM4401-B0 100Base-TX is your wired network.

post your 
```

lshw -C network
```

here so we can see what your network-hardware is.
There should be a driver available in system>administration>something with hardware (sorry am not on gnome atm).

If not, there is ndiswrapper.
Old guides say to edit the file blacklist, wich doesn't exist any more.It it seperated in different blacklist files.

---

### Post by bloodlust757 on 2009-08-01
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: --i removed----
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: -i removed---
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=--i removed--- latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ----i removed-----
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
christian@christian-laptop:~$ 


that is my output
awaiting ur next command star captain

---

### Post by realzippy on 2009-08-02
Your wifi hardware is:
Intel 3945ABG

You are using Jaunty?Then google for "Intel 3945ABG Jaunty"...
Your problem seems to be well known.In a german forum somebody said,
linux-backports-modules-jaunty would solve the problem,try it:

sudo apt-get install linux-backports-modules-jaunty

---

### Post by bloodlust757 on 2009-08-02
ok i did the command butttt sadly i cant test my connection right now... i have a few torrents going. ill test soon

---

### Post by realzippy on 2009-08-02
...dont forget to restart before testing.

---

### Post by bloodlust757 on 2009-08-02
will do
thanks for your help. ill let you no if it works or not

---

