---
title: "Internet stopped working"
date: 2009-08-08
forum: General Help
---

### Post by Tanner2007 on 2009-08-08
I did not know rather to post here or in the network section, but its not really networking, its just internet, anyways i have a fresh install of ubuntu, so now im dual boot with windows vista, so in windows vista internet works fine...but when i switch into ubuntu the internet does not work anymore, even tho it used to. NOTHING internet related..i cant ping do updates or even access websites on firefox,  uninstalled all apps i have that relate to anything internet. and nothing

what should i do

---

### Post by Tclarkie on 2009-08-08
how is your internet security set up

---

### Post by Tek-E on 2009-08-08
it may be a long shot but you could try

```

ifconfig eth0 up

```

---

### Post by Tanner2007 on 2009-08-08
> **Tclarkie said:**
> how is your internet security set up

ubuntu wise, nothing, router wise 63 char long wpa2 pass word and mac filtering, but the desktop which has vista hat works fine and ubutnu which internet does not, both should work, i mean same pc so mac filtering is not it, and internet works for vista and should work for it, i even tried to set it p myself

> **Tek-E said:**
> it may be a long shot but you could try

```

ifconfig eth0 up

```



done it plenty of times, and nothing

---

### Post by Tclarkie on 2009-08-08
try fiddling the password into password and encription accessory

---

### Post by Tanner2007 on 2009-08-08
> **Tclarkie said:**
> try fiddling the password into password and encription accessory

do you mean router? if so i preferred no to change anything if is wired, and not when the inernet used to work like a week ago

---

### Post by Tclarkie on 2009-08-08
> **Tanner2007 said:**
> do you mean router? if so i preferred no to change anything if is wired, and not when the inernet used to work like a week ago
  Application/accessories/keys and and encriptions

---

### Post by Tek-E on 2009-08-08
wait its wireless internet?

---

### Post by chanidu87 on 2009-08-08
> **Tanner2007 said:**
> I did not know rather to post here or in the network section, but its not really networking, its just internet, anyways i have a fresh install of ubuntu, so now im dual boot with windows vista, so in windows vista internet works fine...but when i switch into ubuntu the internet does not work anymore, even tho it used to. NOTHING internet related..i cant ping do updates or even access websites on firefox,  uninstalled all apps i have that relate to anything internet. and nothing

what should i do

Your Internet connection may have been blocked, by the way, is it working your LAN connection (if any)?

---

### Post by Tanner2007 on 2009-08-08
It is wired, NOT WIRELESS , and idk maybe, the network connection ays its connected and gives me an ip and everything, even when i typed in the info Manuel, but yet nothing internet related works. i installed a few firewalls but uninstalled them.

---

### Post by Tclarkie on 2009-08-08
how long has this been happening

---

### Post by Tanner2007 on 2009-08-08
> **Tclarkie said:**
> how long has this been happening

1 week

---

### Post by soapBAR2 on 2009-08-08
It's possible your system isn't set to dhcp. In the command line, try

```
sudo dhclient
```

And if your internet starts working after this, then you'll need to configure your /etc/network/interfaces. To do this,

```
sudo nano /etc/network/interfaces
```

and change "iface eth0 inet SOMETHING" to "inet eth0 inet dhcp". If this doesn't work, please post the outputs of 

```
ifconfig
```
```
sudo dhclient
```
and the contents of
```
/etc/network/interfaces
```

---

### Post by Tanner2007 on 2009-08-08
ill try those steps above but something wierd happen

now it shows on the top network bar, device not managed even when theres a connection there


this is pissing me off

---

### Post by Tanner2007 on 2009-08-08
ill try those steps above but something wierd happen

now it shows on the top network bar, device not managed even when theres a connection there


this is pissing me off

---

### Post by zipperback on 2009-08-08
Please also post the output from the following commands:

> 
lspci
lsusb
ifconfig
iwconfig


Have you recently made any changes to your firewall configuration?

Please provide the output from the following command:

> 
sudo iptables --list


Are both ends of your network cable properly plugged in? Do you have a light on your router for the network connection?

- zipperback
:popcorn:

---

### Post by Tanner2007 on 2009-08-08
double post

---

### Post by Tanner2007 on 2009-08-08
> **zipperback said:**
> Please also post the output from the following commands:



Have you recently made any changes to your firewall configuration?

Please provide the output from the following command:



Are both ends of your network cable properly plugged in? Do you have a light on your router for the network connection?

- zipperback
:popcorn:

I would but them but have no way of getting them from m ubuntu to my laptop, and way to much to type, but now my network manage applet is gone now, wtf im about to just wipe my entire partiton..

---

### Post by soapBAR2 on 2009-08-09
> **Tanner2007 said:**
> I would but them but have no way of getting them from m ubuntu to my laptop, and way to much to type, but now my network manage applet is gone now, wtf im about to just wipe my entire partiton..

Either save them to a flash drive (what you do is type the command and then a > to the file, eg, 
```
iwconfig > /home/tanner2007/iwconfig_log
``` will log the output of iwconfig to /home/tanner2007/iwconfig_log instead of onto the screen - this works with any command) and then copy them here. Or, you could type them out manually...

And yes, manually messing around with /etc/network/interfaces will screw with your network manager. The network manager is nothing more than a nice front-end to that file, so it will obviously get a rude shock when you play with it's baby, but setting it back to normal should fix it.

PS. To get the network manager back, ALT+F2+"network-manager" for Gnome (Ubuntu), and ALT+F2+"knetworkmanager" for KDE (Kubuntu).

---

