---
title: "desktop user passwords in Natty"
date: 2011-07-01
forum: General Help
---

### Post by munnster on 2011-07-01
I just did a clean install of Natty yesterday and have been setting it up for my children and myself. I am trying to set up desktop user accounts for them without them having to put in a password for themselves but have not been able to change this via system/administration/users and groups. Is this a bug or is this feature (turning off passwords at login) turned off in Natty?

Thanks for any information! :)

---

### Post by TeoBigusGeekus on 2011-07-01
I think this is done via Windows options or Login Options (can't remember), not from Users & Groups.

---

### Post by sisco311 on 2011-07-01
> **munnster said:**
> I just did a clean install of Natty yesterday and have been setting it up for my children and myself. I am trying to set up desktop user accounts for them without them having to put in a password for themselves but have not been able to change this via system/administration/users and groups. Is this a bug or is this feature (turning off passwords at login) turned off in Natty?

Thanks for any information! :)

Don't know if it's a bug or not, but users from the **nopasswdlogin** are allowed to log in via GDM without a password. You can use gpasswd to add a user to a supplementary group:
```
sudo gpasswd -a **username** nopasswdlogin
```
Where **username** is the login name of the user.

---

### Post by munnster on 2011-07-01
[QUOTE
```
sudo gpasswd -a **username** nopasswdlogin
```Where **username** is the login name of the user.[/QUOTE]

Great! Thanks!!

---

### Post by sisco311 on 2011-07-01
You're welcome!

---

