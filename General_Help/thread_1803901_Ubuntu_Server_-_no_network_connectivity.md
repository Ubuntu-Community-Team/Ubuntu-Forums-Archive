---
title: "Ubuntu Server - no network connectivity"
date: 2011-07-14
forum: General Help
---

### Post by TimeSpacial on 2011-07-14
I've just installed Ubuntu Desktop and connected the ethernet cable, but I don't have network connectivity. Why?

---

### Post by ikick on 2011-07-14
G'day TrimeSpacial,

Are you able to advise if you've tried connecting other machines using the same cable? Have you installed the drivers for the network card?

Can you post an ifconfig?

Cheers,

D.

---

### Post by papibe on 2011-07-14
You are double posting: [http://ubuntuforums.org/showthread.php?t=1803907]("http://ubuntuforums.org/showthread.php?t=1803907")

---

### Post by TimeSpacial on 2011-07-14
> **ikick said:**
> G'day TrimeSpacial,

Are you able to advise if you've tried connecting other machines using the same cable? Have you installed the drivers for the network card?

Can you post an ifconfig?

Cheers,

D.

Hey dude,

Sure, other machines are able to access the same cable.
The installation has been made in a virtual machine.
Ubuntu desktop is able to connect in the same emulated hardware environment.
Perhaps DHCP was not installed in the installation?


<snip>

---

### Post by papibe on 2011-07-14
> **TimeSpacial said:**
> 
Why don't you go and fhuck yourself in front of your sister and stop trying to be the world police American.

for records.

---

### Post by ikick on 2011-07-14
Hmm - what type of virtualization you using (OpenVZ, VMware etc). It could possibly have something to do with bridging the connection for this specific instance.

---

### Post by TimeSpacial on 2011-07-14
There is nothing wrong with connection bridging. Please see my previous post.

---

### Post by TimeSpacial on 2011-07-14
So, I have done a clean install, logged in, cleared the screen, and performed the following:

[http://i52.tinypic.com/2rh5l3k.png](http://i52.tinypic.com/2rh5l3k.png)

Why can't get I get network connectivity?
I did a clear install of Ubuntu desktop with exactly the same emulated hardware, and it didn't have any problems getting network connectivity what so ever.

Why is Ubuntu Server giving me a head ache straight out of the box?

---

### Post by spynappels on 2011-07-14
please post the output of 
```
ifconfig
```
and 
```
cat /etc/resolv.conf
```

---

