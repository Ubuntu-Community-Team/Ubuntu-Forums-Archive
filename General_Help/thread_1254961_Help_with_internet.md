---
title: "Help with internet"
date: 2009-08-31
forum: General Help
---

### Post by Tenyuu on 2009-08-31
I am looking for help finding wireless networks in my area. I know the information for mine but I do not understand the prompts. Is there a good program to scan for and connect to wireless internet? I am running Ubuntu 9.04.

---

### Post by sideaway on 2009-08-31
network-manager-gnome can scan for networks... I'm unsure what you are having trouble with?

---

### Post by sideaway on 2009-08-31
Which, I might add comes with 9.10, just left click the little wireless icon on the top right and it should produce a list of avaliable wireless networks. Provided your wireless is turned on.

That little icon is the front end of a daemon (background process) called network-manager-gnome.

---

### Post by Tenyuu on 2009-09-01
when I left click all I can see is auto eath0 and VPN connections

there is no on or off switch for the wireless card. also I have network manager and network manager genome.

---

### Post by Sukotto on 2009-09-01
I use Wicd Manager to find and connect to wireless networks.

---

### Post by Tenyuu on 2009-09-01
I tried wicd and it did not help.

---

### Post by Cipher Short on 2009-09-01
Linux does not seem to be reading the  wireless card. There is a light on the back that is not on. I assume  it worked in windows. It seems like I need a driver. Id really like to not have to take it apart to find out what kind of card it is. any suggestions?

---

### Post by P4man on 2009-09-01
run

```
lspci
```

in a terminal to view all internal devices (including network cards). and

```
lsusb
```

to view usb devices. 
You can also run

```
ifconfig
```

to see if your wireless card is detected and has a working driver (look for a wlanX entry).

---

