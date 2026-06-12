---
title: "Set up ndiswrapper automatically?"
date: 2006-04-17
forum: General Help
---

### Post by Airjoe on 2006-04-17
Hello,
  I have ndiswrapper working, but whenever I reboot I have to do "modprobe ndiswrapper", then "iwconfig wlan0 essid (my essid)", and then "dhclient wlan0". Now, obviously it's not the worst thing in the world, but it gets annoying. Can I set it up to do this automatically?

---

### Post by uteck on 2006-04-17
Add ndiswrapper to /etc/modules so it loads during boot.
Check /etc/networking/interfaces and look for the wlan0 entry, I think wlan is kept there also.  If so then make sure it has 'auto' in the config.  Look at the eth0 line as an example.

---

### Post by Airjoe on 2006-04-17
I edited /etc/modules and put in ndiswrapper, but I'm not sure what to do in /etc/network/interfaces. The file is shown below:

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

[end file]

What exactly do I add? Just "auto wlan0"?

Thanks!

---

### Post by susanne on 2006-04-18
Hello Airjoe, I edited my etc/network/interfaces like this and it works fine with ndiswrapper:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

mapping hotplug
script grep

map wlan0


#The wireless network interface
auto wlan0
iface wlan0 inet static 
wireless-essid xxx
wireless-key xxx
wireless-keymode xxx
address xxx
netmask xxx
gateway xxx


iface lo inet loopback

auto lo



If you use dhcp and not a static IP you don´t need the adress, netmask and gateway. I hope this could help for your problem.
Susanne

---

### Post by Airjoe on 2006-04-21
I can't seem to get it to work. Here's my /etc/network/interfaces:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map wlan0

auto wlan0
wireless-essid linksys

[end file]

I don't know if tabs matter or not, but I've tried a couple different combonations with tabs and I still can't get it to work. I still need to set the essid via "iwconfig wlan0 essid linksys", and then do "dhclient wlan0". 

Any ideas?

Thanks :]

BTW I do use DHCP, not static.

---

### Post by katana2k on 2006-04-21
i installed everything ok with ndiswrapper, i can see the card and the networks around

but when i do ifup wlan0 i get no DHCPOFFERS recieved.. 

any ideas?

---

### Post by Airjoe on 2006-04-25
Erm, bump?

---

### Post by az on 2006-04-25
[QUOTE=katana2k]i installed everything ok with ndiswrapper, i can see the card and the networks around

but when i do ifup wlan0 i get no DHCPOFFERS recieved.. 

any ideas?[/QUOTE]
Are you using WEP?

The best way to configure your conection is with the gnome networking tool.  Just enable your wireless card there and set your wep.

---

### Post by Airjoe on 2006-04-26
Does anyone know how I have to configure my /etc/network/interfaces file?

---

### Post by az on 2006-04-26
[QUOTE=Airjoe]Does anyone know how I have to configure my /etc/network/interfaces file?[/QUOTE]
That's what the gnome networking tool really does.

---

### Post by Airjoe on 2006-04-29
I don't know why I would use the gnome networking tool, considerring I'm on **K**ubuntu. Not to mention, even if I was using Gnome, your reply was to a different person; and I'm not using WEP either way.

---

### Post by Flowing_air on 2006-04-29
i think i got the similar problem
I have installed networking tool. 

But my wireless card LED never light up. And also i cannot find the modules folder in etc directory...
what wrong with my system.................

---

