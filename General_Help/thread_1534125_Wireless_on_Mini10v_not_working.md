---
title: "Wireless on Mini10v not working"
date: 2010-07-19
forum: General Help
---

### Post by el_heffe on 2010-07-19
OK, I have a Dell Mini 10v that I installed 10.04 on and have installed the restricted drivers for the wireless as well as the bcmwl-kernel-source following the instructions at:

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

Yet, for the life of me I cannot get my wireless to work with my network. I have it working enough to recognize the wireless networks, but I have to use a static IP in order for the internet to work. It's a long story, but basically it goes like this- in order to share the network from my Win7 to work I have to use static IPs.

So, when I get connected to the network I can assign the IP and everything as such: 192.168.4.3/255.255.252.0/192.168.4.1
But when I go to check it out a couple of things happen which confused me.
It is not wlan0 it is eth1. It shows the ip as: 192.168.4.1
The weird part is the Bcast is 192.168.7.255 and the Mask is 255.255.252.0.

When I try to ping the gateway:
```

PING 192.168.4.1 (192.168.4.1) 56(84) bytes of data.
From 192.168.4.3 icmp_seq=1 Destination Host Unreachable
```

So, I am not sure what I am doing wrong, but it confuses the hell outta me. Then when I

```
$ sudo ifconfig eth1 broadcast 192.168.4.1
```

it takes, but still doesn't work.
So then I take it down and back up with

```
$ sudo ifconfig eth1 down
$ sudo ifconfig eth1 up
```

Once it does that still no dice.

```
$ ping 10.5.48.1
connect: Network is unreachable
```

What am I doing wrong? What would be helpful? I have an actual ethernet connection that I can use, I would just prefer to have the wireless working so I not have to keep switching back and forth.

---

### Post by mikewhatever on 2010-07-19
I was wondering, is 252 is '255.255.252.0' is a typo or is it intentional?

---

### Post by el_heffe on 2010-07-19
> **mikewhatever said:**
> I was wondering, is 252 is '255.255.252.0' is a typo or is it intentional?

Quite intentional.  The operational network is on a 252 subnet and as such I have to use it for this...

---

### Post by el_heffe on 2010-07-21
*bump*

I guess I stumped everyone...

---

### Post by snowpine on 2010-07-21
It is a bug; check this page out for more info:

[http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html](http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html)

---

### Post by el_heffe on 2010-07-25
That is the website I followed and couldn't find in my history.  I tried that after updating as far as I could- still no luck.  When I am done updating my OS X side of the mini I will try it a third time, who knows- maybe third times the charm?  Anyways, I am not too worried about it as I got my Hackintosh up & running for now.. just would have preferred to have ubuntu working.

---

### Post by el_heffe on 2010-11-15
Will be marking this one as [Solved due to being a retard].  Wrong password, learning is a lovely thing.](*,)

---

