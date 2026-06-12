---
title: "Admin password problem in ubantu"
date: 2010-04-05
forum: General Help
---

### Post by linux1880 on 2010-04-05
Hi guys i have installed ubantu 10 from inside the windows as any other softwre, everything is fine except I cannot goto root in terminal neither i see any wireless, pls help. Thanks

---

### Post by NightwishFan on 2010-04-05
Ubuntu does not allow logging in as root by default. Log in as your normal user and then run this command to get root privileges.
```
sudo su
```

As for your wireless, first check System -> Administration -> Hardware Drivers for a wireless card driver. If you do not find one there, please tell me the name of your card, and I will help you.

---

### Post by linux1880 on 2010-04-05
Thank you so much NightwishFan, much appreceated.  I am using dell inspiron 1545, it had no problem with ubantu 9, Idon't know what's happening with 10.

also what is the basic differnce when u install ubantu under windows and or when u install after partition ? Could this be the reason that ubantu did not install all the drivers because i install it under windows ?

---

### Post by wojox on 2010-04-05
Run this in the terminal so we all know what card you have:

```
lspci | grep -i net
```

---

### Post by linux1880 on 2010-04-06
I get this in lspci, can't see wireless card
[HTML]root@ubuntu:/home/me# lspci | grep net
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
root@ubuntu:/home/me# [/HTML]

---

### Post by sisco311 on 2010-04-06
> **NightwishFan said:**
> Ubuntu does not allow logging in as root by default. Log in as your normal user and then run this command to get root privileges.
```
sudo su
```



Usually there is no need for a root shell. You can simply prepend sudo to all the commands you would normally run as root. i.e.:
```
sudo apt-get update
```

Also, if you really need a root shell, you should probably start it with
```
sudo -i
```
rather then sudo su or sudo -s.
EDIT: You can type **exit** or press Ctrl+d to exit from the root shell.

For a brief overview of some of the differences between su, su -, and sudo -{i,s} see [unutbu's post]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4").

@OP You can read more about sudo here: [uhelp]community/RootSudo[/uhelp]

---

