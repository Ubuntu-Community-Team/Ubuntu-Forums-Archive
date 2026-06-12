---
title: "root password issue"
date: 2009-10-30
forum: General Help
---

### Post by n3rxs on 2009-10-30
I did a search and didn't find anything on this but I have noticed in all releases of 9.10 that if you use the user and groups gui manager to set the root password it never takes.

You have to manually set root password from terminal.

---

### Post by jrrader on 2009-10-30
in terminal 

```
sudo passwd
```

edit: I missed where you said you had to set it in terminal.  But at lease anyone who is looking will find it.  Also, you no longer have to set up logging in as root in the login dialogue.  Once you set a password, you can log in as root.

---

### Post by Iowan on 2009-10-30
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by lavinog on 2009-10-30
Please read the link Iowan gave.
There should be no reason to enable the root account.

---

### Post by cariboo on 2009-10-30
> **jrrader said:**
> in terminal 

```
sudo passwd
```

edit: I missed where you said you had to set it in terminal.  But at lease anyone who is looking will find it.  Also, you no longer have to set up logging in as root in the login dialogue.  Once you set a password, you can log in as root.

Unfortunately that only changes the users's password.

---

