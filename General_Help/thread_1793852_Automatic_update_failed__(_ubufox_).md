---
title: "Automatic update failed  ( ubufox )"
date: 2011-06-30
forum: General Help
---

### Post by Noob2011 on 2011-06-30
during the automatic updates i got this error for the update file " ubufox " 

The details are :

------------------------------------------------------
An error occurred

The following details are provided:
E: /var/cache/apt/archives/ubufox_0.9.1-0ubuntu0.10.04.1~mfn3_all.deb: trying to overwrite '/etc/xul-ext/ubufox.js', which is also in package xul-ext-ubufox 0
----------------------------------------------------

My machine is Dell Inspiron mini netbook.. running ubuntu lucid 10.04 . 

What should i do ...  thanks in advance...

---

### Post by Noob2011 on 2011-07-01
bump ...

---

### Post by Dave_L on 2011-07-01
What's the output from the following command?

```
sudo apt-get -f install
```

---

### Post by Noob2011 on 2011-07-01
----------------------------------------
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
---------------------------------------


Thankx

---

### Post by kamaji792 on 2011-07-01
Hi Dude,

I was having a similar problem for a while (days).  Ignored it till the flash stopped working and then started searching for a solution.

I found a thread that suggested:
```
sudo apt-get remove xul-ext-ubufox
sudo apt-get install ubufox
```

I actually just used the fist line and that allowed the flash to install and everything seems fine.

The thread is [http://ubuntuforums.org/showthread.php?p=10988277](http://ubuntuforums.org/showthread.php?p=10988277)

atb K

---

### Post by Noob2011 on 2011-07-01
Thanks a lot mate, That worked. problem solved.... :)

Cheers...

---

