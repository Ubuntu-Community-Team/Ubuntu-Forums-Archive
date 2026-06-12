---
title: "samba questions vista"
date: 2010-01-01
forum: General Help
---

### Post by sdowney717 on 2010-01-01
I have samba network sharing working between an ubuntu box and an xp laptop.
xp laptop does not need login when booting up.

however, a vista laptop does not even show-discover the ubuntu machine
the vista laptop you logon with a password to use when booting up.
both xp and vista laptops are on the wireless LAN and the ubuntu box is on the wired LAN.
internet works on all 3

So what to do with vista box to make it even see the ubuntu box?
Vista laptop did discover several upnp softwares running on the ubuntu box, but does not see the ubuntu shares, etc...

---

### Post by cariboo on 2010-01-01
Have you gone into the network and sharing center in Vista and turned on at least network discovery and file sharing?

---

### Post by VastOne on 2010-01-01
> **sdowney717 said:**
> I have samba network sharing working between an ubuntu box and an xp laptop.
xp laptop does not need login when booting up.

however, a vista laptop does not even show-discover the ubuntu machine
the vista laptop you logon with a password to use when booting up.
both xp and vista laptops are on the wireless LAN and the ubuntu box is on the wired LAN.
internet works on all 3

So what to do with vista box to make it even see the ubuntu box?
Vista laptop did discover several upnp softwares running on the ubuntu box, but does not see the ubuntu shares, etc...

Can you connect to to it via IP? When you try to connect a new drive and you type in the Ubuntu IP address does it then show you the shares on Ubuntu?  I have this same issue with Win 7 to Ubuntu bit I can connect no problem via IP address.

---

### Post by sdowney717 on 2010-01-02
vista laptop also does not see xp laptop shares.
but it does see mediatomb running on ubuntu box
I did turn on file sharing, and the network discovery is on.
what about opening using ip, is this like mapping network drive?
the ubuntu box is pingable

---

### Post by sdowney717 on 2010-01-02
i tried typing in 
\\scott-desktop\Videos as in mapping a network drive but did not work

I tried typing in 
192.168.1.100 but it said this is not a folder

---

