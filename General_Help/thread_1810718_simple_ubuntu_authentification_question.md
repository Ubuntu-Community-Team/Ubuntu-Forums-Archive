---
title: "simple ubuntu authentification question"
date: 2011-07-23
forum: General Help
---

### Post by pain.reign on 2011-07-23
when i try to use wifi in order to connect to preconfigured in network manager settings it requires me to use my ubuntu password every time. How do i disable it?

wpa pass already pre configured i select connect to hidden network, in connection i select preconfigured connection and then i requires to enter my ubuntu user password. i don't want to do it every time. How to make it work withought password?

---

### Post by TeoBigusGeekus on 2011-07-23
I think is the gnome keyring that's asking your password.
Try going to network connections, find your wireless connection and make it available to all users.

---

### Post by gandaran on 2011-07-23
> **pain.reign said:**
> when i try to use wifi in order to connect to preconfigured in network manager settings it requires me to use my ubuntu password every time. How do i disable it?

wpa pass already pre configured i select connect to hidden network, in connection i select preconfigured connection and then i requires to enter my ubuntu user password. i don't want to do it every time. How to make it work withought password?
that's the keyring password, remove the present keyring in passwords and encryption keys then next time set a blank password for the keyring instead, it won't bother you anymore.

---

### Post by pain.reign on 2011-07-23
I don't get what u say. but it seems to me u don't get what i say too. i get this message:

an application is attempting to perform an action that requires priveliges. Authentication is required to perform this action.

I cannot drop anything because i specified only network name and its password. if i remove password isn't it obvious i have to enter it every time and its very long. so i don't want to enter it every time.

And i check available for all that doesn't help.

---

### Post by Tea4all on 2011-07-23
There's 2 passwords, one is your wireless password, and the other is an encryption password so that people can't steal it from the computer. Only matters really if it is stolen.

---

