---
title: "apt-get unmet dependencies problem"
date: 2009-08-05
forum: General Help
---

### Post by avilanchee on 2009-08-05
installed sqlite3 . need libsqlite3-dev to install sqlite3-ruby gem


avinash@SKYLINE:~$ sudo apt-get install libsqlite3-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsqlite3-dev: Depends: libsqlite3-0 (= 3.6.10-1) but 3.6.10-1ubuntu0.2 is to be installed
E: Broken packages

---

### Post by zvacet on 2009-08-05
```
sudo apt-get -f install
```

---

### Post by wojox on 2009-08-05
sqlite 2 is already installed by default if that matters.

---

### Post by avilanchee on 2009-08-05
tried apt-get -f install .. but in vain  .. installed sqlite3 .. libsqlite3-dev is required to build sqlite-ruby gem

---

### Post by avilanchee on 2009-08-06
guys my mistake .. few days back my update manager closed and complained about security packages 

It had remove the security repositories from my sources.list

added it again and its working fine .
Thanks for the effort! Happy Ubunting

Thanks,
Avinash

---

