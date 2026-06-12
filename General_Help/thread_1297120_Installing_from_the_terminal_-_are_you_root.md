---
title: "Installing from the terminal - are you root?"
date: 2009-10-21
forum: General Help
---

### Post by alan_uk on 2009-10-21
I am trying to install the Eucalyptus Framework. I get the following message. I thought that the root password was no longer used with Ubuntu

alan@alan-desktop:~$ apt-get install eucalyptus-cloud eucalyptus-cc
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
alan@alan-desktop:~$ 


Thanks
Al

---

### Post by DeMus on 2009-10-21
> **alan_uk said:**
> I am trying to install the Eucalyptus Framework. I get the following message. I thought that the root password was no longer used with Ubuntu

alan@alan-desktop:~$ apt-get install eucalyptus-cloud eucalyptus-cc
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
alan@alan-desktop:~$ 


Thanks
Al

type sudo in front of it and type your password. It"ll work then.

---

### Post by Niko Johnson on 2009-10-21
su - 
su 
or 
su root

they all log you in as root... assuming you know the root password.. if not you might have to change it with

```
 sudo passwd root 
```
of course you can just type sudo in front of every command.. but that gets a little annoying sometimes

---

### Post by oldos2er on 2009-10-21
> **Niko Johnson said:**
> su - 
su 
or 
su root

they all log you in as root... 

 Only if the OP has enabled the root account, which tends to be frowned on here.

---

### Post by alan_uk on 2009-10-21
Many thanks installed well

Al

---

