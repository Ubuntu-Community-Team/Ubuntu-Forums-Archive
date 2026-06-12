---
title: "stop autoboot"
date: 2011-02-25
forum: General Help
---

### Post by Arushan on 2011-02-25
how do i stop autoboot of ubuntu? and when i try do " su " in the terminal and i enter my password it says failed authentication

but i logged out and logged in again with the password and it worked? is there a default password

---

### Post by thesavager on 2011-02-25
Go to "System" > "manager" > "startup manager" ... there you can change the autoboot of Ubuntu.

BTW ... su command doesn't work, cause Ubuntu doesn't use a root password by default .... you have to do:   sudo su ..then use your user-password.

---

### Post by WorMzy on 2011-02-25
You con use ```
sudo -i
``` instead of su.

---

### Post by Arushan on 2011-02-26
> **thesavager said:**
> Go to "System" > "manager" > "startup manager" ... there you can change the autoboot of Ubuntu.

BTW ... su command doesn't work, cause Ubuntu doesn't use a root password by default .... you have to do:   sudo su ..then use your user-password.


There is no "manager" under system its only Preferences and Administration and there is no startup  manager under those

---

### Post by wilee-nilee on 2011-02-26
> **Arushan said:**
> There is no "manager" under system its only Preferences and Administration and there is no startup  manager under those

You need to install it.
sudo apt-get install startupmanager

---

