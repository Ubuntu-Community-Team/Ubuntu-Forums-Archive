---
title: "Change host name in Ubuntu10.04"
date: 2010-05-22
forum: General Help
---

### Post by digachan on 2010-05-22
I want to change the host name but cannot find where I can change it.
There is no System>Administration>Network in V10.04?

---

### Post by dcstar on 2010-05-22
> **digachan said:**
> I want to change the host name but cannot find where I can change it.
There is no System>Administration>Network in V10.04?

```
gksudo gedit /etc/hostname
gksudo gedit /etc/hosts
```

---

### Post by James78 on 2010-05-22
You can view your current hostname via the command hostname.

To change the name permanently... Edit /etc/hostname with your new hostname.

---

### Post by digachan on 2010-05-22
> **dcstar said:**
> ```
gksudo gedit /etc/hostname
gksudo gedit /etc/hosts
```
 
Hi David,
 
Thanks for the reply and I am little bit new to Linux.
But in the Terminal I typed the above two lines and restarted the PC
but the host name is still the old.

---

### Post by wojox on 2010-05-22
> **digachan said:**
> Hi David,
 
Thanks for the reply and I am little bit new to Linux.
But in the Terminal I typed the above two lines and restarted the PC
but the host name is still the old.

Those commands dcstar gave you let you edit the files to change the old name to the new one. :)

---

### Post by digachan on 2010-05-22
> **digachan said:**
> Hi David,
 
Thanks for the reply and I am little bit new to Linux.
But in the Terminal I typed the above two lines and restarted the PC
but the host name is still the old.
 
Thanks everybody!
I got it and now it is OK!

---

### Post by killboymota on 2010-11-30
i dont get it...

sudo hostname
myhostname
then sudo nano /etc/hosts

127.0.0.1 myhostname
127.0.1.1 myhostname

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Then sudo nano /etc/hostname

myhostname hostname -F /etc/hostname

but i still see croot@(none): ~ 

any ideas?

---

