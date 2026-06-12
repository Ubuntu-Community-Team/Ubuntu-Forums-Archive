---
title: "Wireless WPC11 v4 (RTL8180) WEP Problem"
date: 2006-03-20
forum: General Help
---

### Post by Torquemada on 2006-03-20
Hiya,
I've been using Breezy happily for a while now. Decided to try my linksys WPC11 (v4) PCMCIA card in my laptop. I set it up using ndiswrapper and the Windows XP driver. Works fine, can see the access point and connect to it when WEP encryption in turned off on the AP.

So basically, it works perfectly with WEP turned off.

The problem arises when I turn WEP on on the AP. Using 128 bit encryption I generate a hex key (the same key I use on the XP install on the same machine) and enter it into the network settings dialog box in Gnome.

No dice.

It won't talk to the AP. I can see the AP with iwlist fine, but it just doesn't seem to want to connect using WEP. I manually enter the key into etc/network/interfaces with the same result. I've also tried changing the key to uppercase, lowercase, seperating every 4th character with a hyphen... to no avail. I've also tried using a 64 bit key, which didn't work either.

It's driving me nuts, as you can imagine. I've searched the forums and Google high and low for an answer, but came up empty-handed.

Anyone have any ideas? I'd greatly appreciate it.

---

### Post by ringjp on 2006-05-02
I'm having the same problem, anybody have any ideas?

---

### Post by dmizer on 2006-05-02
have you tried adding the wep key manually via the command line?

ie:
```
sudo iwconfig eth1 inserthexkeyhere
```
if eth1 is not your wireless card, replace it as necessary.

---

### Post by monomaniacpat on 2006-05-02
Or...

```
sudo iwconfig wlan0 mode managed essid Your_Router_Name_Here key WEP_Key_Here
```

---

