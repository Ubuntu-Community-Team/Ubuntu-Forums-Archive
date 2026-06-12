---
title: "problem with wireless at startup"
date: 2006-02-17
forum: General Help
---

### Post by dphipps on 2006-02-17
I have a wireless car in my computer and it is working.  However, everytime I restart it will not work again untill I run the following camands.

```
sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 essid phipps2
sudo iwconfig wlan0 channel 3
sudo /sbin/ifconfig wlan0 192.168.3.77
sudo /sbin/route add default gw 192.168.3.1 wlan0
```

Any ideas about what I can do to fix this.

---

### Post by TheIdiotThatIsMe on 2006-02-17
Do you happen to use ndiswrapper for your wireless card?

EDIT: You can try this:

```
sudo gedit /etc/network/interfaces
```
And add an entry that looks like this:
```
iface wlan0 inet dhcp
wireless-essid XXXXXXXXXXX
wireless-key XXXXXXXXXXX
```
Then at the **auto** line add wlan0 ;)

---

### Post by dphipps on 2006-02-18
> Then at the auto line add wlan0
What is the auto line and what do I add to it.

```
iface wlan0 inet dhcp
wireless-essid XXXXXXXXXXX
wireless-key XXXXXXXXXXX
???
```

---

### Post by TheIdiotThatIsMe on 2006-02-19
[QUOTE=dphipps]What is the auto line and what do I add to it.

```
iface wlan0 inet dhcp
wireless-essid XXXXXXXXXXX
wireless-key XXXXXXXXXXX
???
```[/QUOTE]

The auto line is simply a line of text that begins with the word auto. Then add the word wlan0 to the line.

The code above will have those settings loaded when you boot your computer. Your essid is the name of your network, and the wireless key is your WEP key.

---

