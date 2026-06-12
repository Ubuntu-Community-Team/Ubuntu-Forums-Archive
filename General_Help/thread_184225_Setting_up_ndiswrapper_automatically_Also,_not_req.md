---
title: "Setting up ndiswrapper automatically? Also, not require login after restart?"
date: 2006-05-29
forum: General Help
---

### Post by Airjoe on 2006-05-29
I can't seem to get ndiswrapper to automatically setup my network.
Here's my /etc/network/interfaces:

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

BTW I do use DHCP, not static.


Also, is there a way I can disable the requiring of a login after a reboot? See, I use my linux computer as a server; it doesn't have a monitor, keyboard, or mouse. I just connect to it with SSH. These two things are throwing me off. 

Thanks :]

--Airjoe

---

### Post by az on 2006-05-29
> **Airjoe]I can't seem to get ndiswrapper to automatically setup my network.
Here's my /etc/network/interfaces:

# 
BTW I do use DHCP, not static.


Also, is there a way I can disable the requiring of a login after a reboot? See, I use my linux computer as a server said:**
> 

--Airjoe

Thw wlan0 stanza should be

auto wlan0
iface wlan0 inet dhcp
wireless-mode managed
wireless-essid linksys


Is the ndiswrapper module being loaded for you every time you boot?


And you do not have to log in locally to be able to ssh into your box.  Sshd is run every time you boot if it is installed.  The ssh client is installed by default, but the server is not.

sudo apt-get install ssh

to install the ssh server.

---

