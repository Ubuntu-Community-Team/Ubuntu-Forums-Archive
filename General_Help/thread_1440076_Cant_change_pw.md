---
title: "Cant change pw"
date: 2010-03-27
forum: General Help
---

### Post by altjx on 2010-03-27
When I go to terminal and type "passwd" I get this
```
(current) UNIX password: 
passwd: System error
passwd: password unchanged

```

Worked before, not sure whats goin on now.

---

### Post by karthick87 on 2010-03-27
Try

```
sudo passwd <username>
```

---

### Post by altjx on 2010-03-27
> **getyourkarthick said:**
> Try

```
sudo passwd <username>
```

```
alt@alt-linux:~$ sudo passwd alt
passwd: System error
passwd: password unchanged

```

---

### Post by karthick87 on 2010-03-27
*Run sudo dpkg-reconfigure -plow libpam-runtime
*Deselect "Winbind NT/Active Directory authentication"
*Select OK

and then try again..

---

### Post by altjx on 2010-03-27
Worked perfectly, thanks.

---

### Post by altjx on 2010-03-27
> **getyourkarthick said:**
> *Run sudo dpkg-reconfigure -plow libpam-runtime
*Deselect "Winbind NT/Active Directory authentication"
*Select OK

and then try again..

Does this mess anything up as far as connecting over the network? When I go to Places > Network, it gives me this error.

Error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Please select another viewer and try again.

---

