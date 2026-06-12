---
title: "login"
date: 2011-08-10
forum: General Help
---

### Post by invader.sushil on 2011-08-10
i created a user **apache** in group **apache** and by useradd and groupadd command. i am working on a user called **server **and group is also **server**. The login screen shows both the users **apache** and **server**. My concern is that if sombody has the password to the username **apache, **hecan login. How do you disable user **apache** on the login screen so that it only shows user **server**.

---

### Post by Bart92 on 2011-08-10
> **invader.sushil said:**
> i created a user **apache** in group **apache** and by useradd and groupadd command. i am working on a user called **server **and group is also **server**. The login screen shows both the users **apache** and **server**. My concern is that if sombody has the password to the username **apache, **hecan login. How do you disable user **apache** on the login screen so that it only shows user **server**.

There is a gconf setting for it


sudo -u gdm gconftool-2 --type bool --set /apps/gdm/simple-greeter/disable_user_list 'true'


or

sudo usermod -u 999 [username]

---

### Post by deathadder on 2011-08-10
I'm not sure how to remove login names from GDM, but if you want to make sure nobody can login using the apache user you can set their shell to /bin/false like so:
```
sudo usermod -s /bin/false apache
```

---

### Post by sanderd17 on 2011-08-10
If someone is clever enough to get your password, he'll also be clever enough to do a 
```

su apache

```
and login as "apache" without the graphical login manager.

Anyway,

I suppose you're using GDM (the default login manager)? If you use KDM or LightDM, this will be different. But for GDM you can launch the gconf-editor (press ALT+F2 and type the name). Then go to apps -> GDM and you should find some settings.

---

