---
title: "Home Networking Again"
date: 2010-09-01
forum: General Help
---

### Post by colrakeshgupta on 2010-09-01
I am on following computers

[LIST]
[*]Sony Vaio CR 363 running Lucid with Wired Broadband ( BSNL India )
[*]HP Compaq Desktop running Win XP on BSNL HSPA Wireless
[*]Acer Desktop running WinXP
[/LIST]
I want to network all three and share HP 1007 printer
I am new to Ubuntu and Linux
I have read extensively on Ubuntuforums as well as google it
Certain solutions were there but I could translate them to Solutions !
Could I be please helped ?

---

### Post by endotherm on 2010-09-01
do you have a router of some kind or  does the wireless BSNL device connect all three devices? 

network configuration has come a long way in the last few years, and while there are many options, now a days you can often just plug the devices in. 

you can test this, by opening a terminal on one pc, and "pinging" another computer by name (you should have set the computer name during install).
```

ping -c3 <remote-computer-name>

```

if it works it should look somthing like this:
```

Lucid:~$ ping -c3 localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.360 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.058 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.063 ms


```


once you have that working, you network is there and active, so you will then have to share and configure the printer. I'm afraid I have little expertise on this, but hopefully someone who does will be by shortly.

---

### Post by sikander3786 on 2010-09-01
From which PC you want to share the printer? Ubuntu, Vista or XP? There are many possiblities so please be a little more specific.

As far as I have read about HP Laserjet P1007 it doesn't have an ethernet port. Correct me if I am wrong.

---

