---
title: "Authentication failure on users and groups"
date: 2010-05-08
forum: General Help
---

### Post by wayne@chicago on 2010-05-08
Greetings!
I upgraded from 8.04LTS to 10.04LTS desktop. I can do sudo as root at the terminal, but I can't pass authentication trying to add a user (System->Administration->Users and Groups). 

Here is what I got:
An error occurred while checking for authorizations: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
You may report this as a bug.

Any ideas?

---

### Post by kio_http on 2010-05-08
> **wayne@chicago said:**
> Greetings!
I upgraded from 8.04LTS to 10.04LTS desktop. I can do sudo as root at the terminal, but I can't pass authentication trying to add a user (System->Administration->Users and Groups). 

Here is what I got:
An error occurred while checking for authorizations: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
You may report this as a bug.

Any ideas?

If its a bug in GNOME User management.

add your user from terminal
```
sudo useradd -G admin yourusername
```
or if you want more options, in a GUI way, install the Kde User management component and run it.
```
sudo apt-get install kuser
```
then
```
gksu kuser
```

---

### Post by Gb Knight on 2010-05-09
I tried the sudo - G etc....
does not seem to make a difference.

When pressing ctrl+alt+F1 i get : GDM-binary [982] warning: unable to find users: no seat id found

Also if I try apt-get install kuser, it simple won't install

Thanks for your help

---

### Post by Zireth ZH on 2010-05-09
HA! i ran away from open suse cuz of that ... someone post the solution xD

---

### Post by wayne@chicago on 2010-05-13
Thanks. Kuser works great for me.

---

