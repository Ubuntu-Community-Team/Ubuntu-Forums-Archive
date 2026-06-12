---
title: "Check if ip 192.168.x.x from lan is online"
date: 2010-03-16
forum: General Help
---

### Post by Sycron on 2010-03-16
I need something like that```
checkip 192.168.3.44 >> ip.txt
```
ip.txt: ON!

And with that i wish to see if my sister's computer is connected to the internet. Any help would be useful.

A ping based solution is ok but i need things like returning 0 for pc not connected to internet and 1 otherwise.

---

### Post by uylug on 2010-03-16
> **Sycron said:**
> I need something like that```
checkip 192.168.3.44 >> ip.txt
```ip.txt: ON!

And with that i wish to see if my sister's computer is connected to the internet. Any help would be useful.

A ping based solution is ok but i need things like returning 0 for pc not connected to internet and 1 otherwise.

sudo nmap -sP 192.168.3.44?

or maybe...

sudo nmap -sP 192.168.3.1-255

---

### Post by The Real Dave on 2010-03-16
I've got the perfect script for you :) I was originally for conky, but it'll work stand alone too :)

[Here you go.]("http://linuxexpresso.wordpress.com/2009/12/20/conky-ip-monitor/")

If you like it, leave a comment :)

---

### Post by Sycron on 2010-03-16
VERY useful. Thanks.

---

### Post by tgalati4 on 2010-03-16
sudo apt-get rwho  (install on both local and remote machines)
ruptime

---

### Post by rnerwein on 2010-03-16
hi
the ping stuff only tells you if the pc is up and not if the pc is connected to the internet. ping is a very
low level command works deep on the ip stack.
you should use "iftop" to see the traffic between the pc and the router.
or the harder they come: tcpdump or driftnet
ciao

---

