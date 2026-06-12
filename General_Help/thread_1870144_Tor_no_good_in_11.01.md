---
title: "Tor no good in 11.01"
date: 2011-10-26
forum: General Help
---

### Post by jimmyBoy18 on 2011-10-26
I have followed the directions from this site, from the Tor site, and from 3rd party sites to NO AVAIL!
   I have a dual-boot 64-bit Dell Inspiron 1545 with Natty and Win 7. On the Win side installation was a breeze but I hate Windows and feel like a newb when I use it. I wonder if anyone else has had the same issue...Please Help.    Jim

---

### Post by mikejonesey on 2011-10-26
lol which site and which tutorial, yes tor not straight forward install but it does work and is easy enough... lets see your tutorial (i have tor on a couple of linux partitions but to be honest it is of little use, too slow, i merely installed to test it...)

---

### Post by haqking on 2011-10-26
a friends tutorial should work for ya

[http://dangertux.wordpress.com/tutorials/tor-polipo-5-minute-install-guide-ubuntu-11-0411-10/](http://dangertux.wordpress.com/tutorials/tor-polipo-5-minute-install-guide-ubuntu-11-0411-10/)

---

### Post by jimmyBoy18 on 2011-11-03
NO GOOD....I tried it 3 times. The Tor repository has no packages for "Natty".

---

### Post by haqking on 2011-11-03
> **jimmyBoy18 said:**
> NO GOOD....I tried it 3 times. The Tor repository has no packages for "Natty".

what are you talking about ?

[https://www.torproject.org/docs/debian.html.en](https://www.torproject.org/docs/debian.html.en)

and as in the link i posted you add it to your sources list:

```
deb     http://deb.torproject.org/torproject.org natty main
```

read the link i posted it is easy to install

---

### Post by Dangertux on 2011-11-03
I just double checked that tutorial (since I wrote it) in an Oneiric VM, it works fine. Double check your steps particularly when adding the repo if it's giving error. Remember Linux is case sensitive so Natty is not the same as natty.

---

