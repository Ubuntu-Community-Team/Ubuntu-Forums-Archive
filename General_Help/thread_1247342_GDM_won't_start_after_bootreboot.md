---
title: "GDM won't start after boot/reboot"
date: 2009-08-22
forum: General Help
---

### Post by ghostmac on 2009-08-22
I just did a fresh install of 9.04 on a Toshiba Satellite. Everything went well though once I rebooted the machine, It boots to a command prompt.

I log in and have verified that it is booting to runlevel 2. I look in /etc/init.d/ and gdm is there as well as in the link in /etc/rc2.d (S50gdm). 
I've also tried adding 'gdm &' to the rc.local script, reboot and still get the same behaviour. 

If I login to the shell after a reboot, the only way to get gdm started is with a 'sudo gdm' command. 

Can someone tell me what else I should be looking at?
What I want is to be able to start the machine and have the login manager start. 
Thanks.

---

### Post by tgeer43 on 2009-08-22
I don't know about the actual cause but once you do get to the desktop manually, check to make sure that GDM is checked in System->Administration->Services.

Beyond that I don't know at the moment.

tgeer

---

### Post by id10twork on 2009-08-22
i don't have too much advice on what to do with this, but i'm interested to know if you get it fixed. i had to reinstall mine :-\

---

### Post by ghostmac on 2009-08-23
tgeer43, the service is checked :confused:

I really don't want to re-install but it's looking like I may have to.

---

### Post by sandyd on 2009-08-23
perhaps
```

sudo dpkg-reconfigure gdm

```
is what you need.

---

### Post by ghostmac on 2009-08-23
carlee, I ran that and rebooted. 
GDM still refuses to start.

---

### Post by ghostmac on 2009-08-23
Interesting. When I boot into single user-mode, GDM start just fine.

---

