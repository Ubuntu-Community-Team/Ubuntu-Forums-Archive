---
title: "Can't login after adding new user"
date: 2011-10-14
forum: General Help
---

### Post by Separ on 2011-10-14
I've just installed Ubuntu 11.10 in a virtual machine but the environment I'm using it in requires me to have the same user account name, uid and gid as the other 40-something machines I'm working with as I'm connected to a domain which has Windows and different kinds of Linux machines running on it.

I ran the following after deleting the temporary user I had to create at install:

```
groupadd --gid 1000 domain
useradd --uid 1022 --gid 1000 --home /home/tester --shell /bin/bash tester
passwd tester
```

But now when I try to log in as the new user, I just get kicked back out to the login screen again.

Anyone have any suggestions?

---

### Post by dcstar on 2011-10-14
> **Separ said:**
> I've just installed Ubuntu 11.10 in a virtual machine but the environment I'm using it in requires me to have the same user account name, uid and gid as the other 40-something machines I'm working with as I'm connected to a domain which has Windows and different kinds of Linux machines running on it.

I ran the following after deleting the temporary user I had to create at install:
............
Anyone have any suggestions?

The "Temporary user" is the primary root access user for the whole system and many functions depend on it, you have basically wrecked the system by deleting it.

Reinstall.

---

### Post by Separ on 2011-10-14
I wouldn't think that what you said would be correct. The fact is, this method works on all of the other kinds of Linux systems that we run (CentOS, Fedora, RedHat, Debian, etc.)

The system shouldn't depend on having the same user always there from when you did an install, should it? It just seems silly to me if it does.

I had given the new user administrative rights and also added it to the sudoers file too.

Edit: I've just tried this on the other (32 bit) virtual machine that I created and didn't delete the user that I had installed with. It is getting the same problem.

---

### Post by Separ on 2011-10-14
Ah, just found the problem. Only root was able to write to /tmp because the permissions weren't set on it properly after creating the new user.

```
chmod a+w /tmp
```

No need for reinstall :D

---

### Post by WorMzy on 2011-10-14
/tmp should have it's permissions set to 1777.

```
sudo chmod 1777 /tmp
```

---

### Post by Separ on 2011-10-14
Ah thanks, what I did worked but I've changed it to 1777 :)

---

