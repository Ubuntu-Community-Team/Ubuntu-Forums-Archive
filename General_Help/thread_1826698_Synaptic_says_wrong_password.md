---
title: "Synaptic says wrong password"
date: 2011-08-16
forum: General Help
---

### Post by RefinersFire on 2011-08-16
I downloaded and installed Ubuntu-Server 11.04, then installed XFCE as a light weight, fast desktop. Then I installed Synaptic from apt-get. Now, Synaptic complains that I am entering the wrong password. I cannot log in to Synaptic at all.

---

### Post by jerrrys on 2011-08-17
check this out

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Synaptic+Package+Manager+---+says+wrong+password&sa=Search&cof=FORID:9#941](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Synaptic+Package+Manager+---+says+wrong+password&sa=Search&cof=FORID:9#941)

---

### Post by sisco311 on 2011-08-17
Run:
```
gksu-properties
```
and make sure that the authentication mode is set to sudo.

---

### Post by RefinersFire on 2011-08-17
> **sisco311 said:**
> Run:
```
gksu-properties
```
and make sure that the authentication mode is set to sudo.

Still doesn't work. I just figured out that I could gksu synaptic

---

### Post by Unicast on 2012-01-02
> **sisco311 said:**
> Run:
```
gksu-properties
```
and make sure that the authentication mode is set to sudo.

Thanks, this worked for me with Lubuntu 11.04 where Synaptic refused to accept my admin password.

---

