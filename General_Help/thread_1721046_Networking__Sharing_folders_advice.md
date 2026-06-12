---
title: "Networking / Sharing folders advice"
date: 2011-04-04
forum: General Help
---

### Post by cap10Ibraim on 2011-04-04
I got ubuntu on my desktop now 
there are three other windows laptops , I would like to make a folder for each laptop user with username and password to allow them to store their files on the desktop 
should I use samba or ftp or ... ?

---

### Post by bodhi.zazen on 2011-04-04
I would steer you towards samba ;)

See :

[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)

The most important part of that guide is:

1. you must add each user as a samba user (smbpasswd).

2. Add each share using the private share template. 

Basically it is a matter of adding the users and editing the configuration file.

---

### Post by cap10Ibraim on 2011-04-04
do you suggest to make these folders in my home directory or .. ?

---

### Post by bodhi.zazen on 2011-04-04
Depends a little, in general it does not matter.

It will not work well if your home directory is encrypted =)

In general, on my samba server, I create the shared directories, in something like /share

You could use /share/user1
/share/user2

Or, as long as it is not encrypted, you could put them in your home directory

---

### Post by cap10Ibraim on 2011-04-04
so is this true ?
```

[private]
comment = Private Share
        path = /smbl/Marwa
        browseable = no
        read only = no
	security = Marwa
	encrypt passwords = true
	map to guest = bad user
	guest account = nobody

```
Marwa is a windows user , I created marwa too on my ubuntu desktop and add it to the samba users

---

### Post by bodhi.zazen on 2011-04-04
I do not know the samba syntax without referencing it , but that definition looks good.

A better question is it working as you expect ?

---

### Post by cap10Ibraim on 2011-04-04
yes now every thing is running good , thanks for your help

---

### Post by bodhi.zazen on 2011-04-04
> **cap10Ibraim said:**
> yes now every thing is running good , thanks for your help

Fantastic =)

---

