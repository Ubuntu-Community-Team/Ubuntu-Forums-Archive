---
title: "Default password for root"
date: 2009-08-15
forum: General Help
---

### Post by gugaliashashank on 2009-08-15
Hi,

Can any one tell me default password for root user.

Thanks
Shashank

---

### Post by yeeeev on 2009-08-15
There is none.
You should use sudo and gksu(sudo for gui apps) instead of direct root access. They enable the default user to acquire temporary root privileges and perform root tasks.
Usage examples:
sudo vi /etc/X11/xorg.conf
or
gksu wireshark

---

### Post by tprayush on 2009-08-15
by default there is no password set.....but u can set it explicitly as...go
Administration >> Users & groups then unlock the root...with your password then set the password for 'root' in the properties...

i guess this might work!!!

---

### Post by credobyte on 2009-08-15
By default root account is disabled. More information ( including disadvantages of enabling it ): [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you want to do something as root ( without sudo <command> ):
```
sudo -i
```

---

### Post by tonychen123 on 2009-08-15
Hey, maybe you should try to use command:
```
sudo su
```

---

### Post by Mardoct909 on 2009-08-15
As said above, sudo su gets you in as root. If you then run passwd , you can set a password for root.

---

### Post by Bachstelze on 2009-08-15
OP got his answer, thread closed. More at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

