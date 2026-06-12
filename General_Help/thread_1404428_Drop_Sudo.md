---
title: "Drop Sudo"
date: 2010-02-11
forum: General Help
---

### Post by NiGhtMarEs0nWax on 2010-02-11
is there a way to drop privileged sudo rights? a schellscript or applet? thanks :)

---

### Post by howefield on 2010-02-11
What do you mean by "drop"

Do away with the need for it ?

---

### Post by tom.swartz07 on 2010-02-11
> **NiGhtMarEs0nWax said:**
> is there a way to drop privileged sudo rights? a schellscript or applet? thanks :)

Im assuming you mean when you use
```
sudo su
```

you could 'drop' that simply by typing 
```
exit
```
and it will put you back to your regular account permissions

---

### Post by subodh.rohilla on 2010-02-11
The configuration file is /etc/sudoers , you can edit it to define which user can have sud0 privilege and which don't

---

### Post by audiomick on 2010-02-11
> **subodh.rohilla said:**
> The configuration file is /etc/sudoers , you can edit it to define which user can have sud0 privilege and which don't
be careful messing around in there!

---

### Post by alccode on 2010-02-11
> **audiomick said:**
> be careful messing around in there!

In particular, you should always change sudo privileges by running the special "visudo" command instead of editing /etc/sudoers directly.

---

### Post by mcduck on 2010-02-11
> **subodh.rohilla said:**
> The configuration file is /etc/sudoers , you can edit it to define which user can have sud0 privilege and which don't

Better just remove the user from the "admin" group if you don't want that user to be able to perform admin tasks.. :)

---

