---
title: "what user accounts should i generate?"
date: 2011-10-06
forum: General Help
---

### Post by Karottenbaum on 2011-10-06
hallo,
i installed xubuntu on yesterday... (im a first time user)

my question is:
at the install-process i made one user account.

  isn'tit better to make one desktop-account with no rights to change anxthing and one admin account?

i could sudo with the desktop account if needed!?

how does this sudo/su thing work, that's not an account its just a privilege, right?
which password would a sudo/su command take, the one from the admin account?

do you think its a good idea to make two accounts, admin and desktop-user? i want to be as much secure as possible...

there is also this group-thing i don't quite understand... can somebody explain me that or has a link?

thanks ALOT!

---

### Post by haqking on 2011-10-06
> **Karottenbaum said:**
> hallo,
i installed xubuntu on yesterday... (im a first time user)

my question is:
at the install-process i made one user account.

  isn'tit better to make one desktop-account with no rights to change anxthing and one admin account?

i could sudo with the desktop account if needed!?

how does this sudo/su thing work, that's not an account its just a privilege, right?
which password would a sudo/su command take, the one from the admin account?

do you think its a good idea to make two accounts, admin and desktop-user? i want to be as much secure as possible...

there is also this group-thing i don't quite understand... can somebody explain me that or has a link?

thanks ALOT!

[ROOTSUDO]("https://help.ubuntu.com/community/RootSudo") explains everything pretty much

for groups and user management in general [https://help.ubuntu.com/8.04/serverguide/C/user-management.html](https://help.ubuntu.com/8.04/serverguide/C/user-management.html)

---

### Post by mcduck on 2011-10-06
In general Ubuntu's security model doesn't really require you to create any more accounts than the one you already have; even admin accounts don't run with admin permissions all the time, they only have the ability to temporarily gain admin permissions through the use of *sudo* and a password confirmation. So it's perfectly safe to use that account all the time, you only need non-admin accounts for the users who really don't need to be able to access any system-wide settings.

Sudo uses the user password for that user, and then checks /etc/sudoers file to see if that user has the permission to use sudo to do the specific task you are trying to do.

Su, on the other hand, uses target user's password, so using it for admin tasks would require root password, which doesn't exist on Ubuntu. So you can't use su to gain root privileges.

---

