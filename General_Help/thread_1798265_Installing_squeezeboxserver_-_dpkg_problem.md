---
title: "Installing squeezeboxserver - dpkg problem"
date: 2011-07-06
forum: General Help
---

### Post by castalla on 2011-07-06
Hi!

I need some newbie help/advice please.

> 
user@SmartQ:~$ sudo dpkg -i --no-act squeezeboxserver_7.5.5~32569_all.deb
Selecting previously deselected package squeezeboxserver.
(Reading database ... 5%
dpkg: warning: files list file for package `libffi5' missing, assuming package has no files currently installed.
(Reading database ... 75%dpkg: unrecoverable fatal error, aborting:
 unable to open files list file for package `samba-common-bin': Input/output error
user@SmartQ:~$
 

Where to now?

Thanks

---

### Post by nothingspecial on 2011-07-06
try

```
sudo apt-get install -f
```

---

### Post by castalla on 2011-07-06
Thanks!

I get exactly the same message if I run the install again.

I'm sure that samba is already installed.

---

### Post by nothingspecial on 2011-07-06
Hmmmm

Stabbing in the dark here.....

Are you installing on a 64bit machine?

You may need ia32-libs, it's that long since I installed it I can't remember but I know it gave me an error.

---

### Post by castalla on 2011-07-06
No - it's an arm based tablet running ubuntu 9.04

---

### Post by nothingspecial on 2011-07-06
Ok, give me 15 minutes to download the thing ---- slow speeds

I've been meaning to migrate it to my new server anyway :)

Might as well do it now :P

***Edit, oh says 3 minutes, I'm sure it took longer than that

---

### Post by nothingspecial on 2011-07-06
Don't know what to say. It did give me dependency errors but apt-get install -f fixed them. It's up and running :confused:

---

### Post by castalla on 2011-07-06
I presume it's the weird tablet version of ubuntu - god knows where everything is?

Thanks for your advice ... if you have any other bright ideas ... !?

---

