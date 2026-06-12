---
title: "How do I find out my IP address?"
date: 2011-11-23
forum: General Help
---

### Post by crazyfuturamanoob on 2011-11-23
This PC is running Ubuntu Server 10.10 but there is no monitor.
How can I find out its IP address?
Thx :)

---

### Post by WorMzy on 2011-11-23
Run ```
ifconfig
```

---

### Post by crazyfuturamanoob on 2011-11-23
> **WorMzy said:**
> Run ```
ifconfig
```

Yes yes but there is no monitor.

---

### Post by WorMzy on 2011-11-23
ssh in first then. o_O

---

### Post by jawilljr on 2011-11-23
One way is to install nmap:

```
sudo apt-get install nmap
```

Then run rhis command:

```
nmap -sP 192.168.1.1-254
```

Change '192.168.1.1' to whatever your LAN is.

Jerry

---

### Post by mikejonesey on 2011-11-23
just to chuck another one in, i prefer arp-scan over nmap (for lan tasks)...

---

### Post by BC59 on 2011-11-23
It's like to be blind. You have the IP but you cannot see it because there is no monitor.

A solution could be by printing the screen. 

Do a ipconfig and then push print screen. Then ok and then export the .png to a usb, something like cp* and all this through terminal CTRL+ALT+T.

Good Luck!

---

### Post by cortman on 2011-11-23
er, put a monitor on it?

---

### Post by crazyfuturamanoob on 2011-11-23
I finally bothered to connect a monitor and got the IP address. Actually this PC wasn't booting OS at all due to misconfigured BIOS. I also noticed the 127 °C temperature and random shutdowns.
So that's why I got this PC for free. :)

---

