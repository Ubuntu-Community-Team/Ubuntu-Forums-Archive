---
title: "Activate wifi at startup"
date: 2011-02-19
forum: General Help
---

### Post by san000 on 2011-02-19
Hello, 

Is there any way to automatically activate the wifi at system startup without using the keyboard switch?

I have tried this script in gedit, saved as .run and added to startup applications but it doesn't work: 

dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set string:org.freedesktop.NetworkManager string:WirelessEnabled variant:boolean:true




thanks

---

### Post by san000 on 2011-02-20
Up. I need help with this.

---

### Post by coldraven on 2011-02-20
What version of Ubuntu are you using?
All my wi-fi connections just start automatically.
Have you ticked "connect automatically" in Network Connections?
System>Preferences>Network Connections

---

### Post by san000 on 2011-02-20
Yes I do, but that is to activate the connection. What I need is a script to enable the wireless card at startup (instead of using the keyboard switch)

I run Ubuntu 10.10.

Laptop: HP G62.

---

### Post by Matt__ on 2011-02-20
can you edit the /etc/network/interfaces to enable wlan to auto start?

there should be a line something like *iface wlan0 inet dhcp*, if its not there add it and see if that works.

---

### Post by san000 on 2011-02-20
There was no such a line in /etc/network/interfaces. I tried to add it and reboot but wifi didn't activated by itself. In fact, network manager icon disappeared and I wasn't able to connect. Needed to delete the line and after a new reboot it was working again. 

Any suggestion?

---

### Post by san000 on 2011-02-21
Up. Any help?

---

### Post by coldraven on 2011-02-21
I have an HP 6715b. The wi-fi is switched on with a touch sensitive part of the panel.
If it's switched on when I power down it then it stays switched on when I power back up.
I can't understand why your system does not do the same. Very odd!
I did read somewhere that on some older machines you had to switch wi-fi on in Windows before installing Ubuntu. Otherwise Ubuntu would not detect the card and the switch would not function afterwards.
What do you call these switches? Hardware? BIOS?

---

### Post by wiggly81 on 2011-02-21
maybe there is an option in the system bios to automatically enable the wi-fi on startup

---

### Post by san000 on 2011-02-21
I tried that, but even enabling the wifi through the bios, when the computer is starting, the wifi light stays on, but when ubuntu starts, it turns off again.

---

### Post by thefasterblueone on 2011-02-21
Please post the reults of:

```
sudo rfkill list all
```

---

### Post by san000 on 2011-02-21
Here it is:
[HTML]
0: hp-wwan: Wireless WAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
[/HTML]

---

