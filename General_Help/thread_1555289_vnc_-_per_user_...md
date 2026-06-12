---
title: "vnc - per user .."
date: 2010-08-17
forum: General Help
---

### Post by vonshavingcream on 2010-08-17
Not sure if this right topic for this, so please move it if I messed up.

this morning at work we came into a problem. Our new firewall was not playing nice with some perl scripts we have running on our web server. We ended up needing to vnc into my ubuntu machine at home to have outside access to the system to test and configure the firewall correctly.

Then this afternoon we needed to mess with https settings for some other remote access stuff and the vnc connection came in handy.

I thought maybe it would be useful to have a vnc or virtual desktop running for each of the three of us at work to access to in case we need it.

My only problem is I can't seem to find any documentation or anything that says how to configure vnc for multiple connections or any other alternative for multiple remote desktops.

I am using tightvnc on ubuntu 10.04

Can anyone point me in the right direction?

Thanks,
P

---

### Post by ercferret18 on 2010-08-17
maybe you could use ssh instead... you can forward X to run gui programs by typing in: "ssh -X <host>". SSH can have multiple users.

---

### Post by vonshavingcream on 2010-08-17
correct me if I am wrong, but this would require me to be using a linux machine at work as well.

While that would work in my case, it will not work for the other applications. for example at one point i was vnc'ing in on a windows machine today, and at another point it was from a mac.

if it is possible I am game for trying it.

C

---

### Post by ercferret18 on 2010-08-17
With Mac, you can use ssh from the terminal. In windows, you can use a combination of PuTTY and Xming

---

