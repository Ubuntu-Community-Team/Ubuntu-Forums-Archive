---
title: "Is it possible to prevent users from changing password?"
date: 2010-02-21
forum: General Help
---

### Post by ubun_two on 2010-02-21
I am just wondering if it's possible to prevent non-admin desktop or unprivileged users from changing their own password, once the admin set one for them.

I am asking this for possibility of using Ubuntu for public PC.  I wouldn't want some user to just change it and prevent other users from logging in. 

Thanks!

---

### Post by Darkish Dave on 2010-02-21
> **ubun_two said:**
> I am just wondering if it's possible to prevent non-admin desktop or unprivileged users from changing their own password, once the admin set one for them.

I am asking this for possibility of using Ubuntu for public PC.  I wouldn't want some user to just change it and prevent other users from logging in. 

Thanks!

KDE has a kiosk mode: [http://extragear.kde.org/apps/kiosktool/](http://extragear.kde.org/apps/kiosktool/)

---

### Post by ubun_two on 2010-02-21
I am hoping of the way to still give users the desktop (for uses of OpenOffice, among other things).

Is there any ways without going into kiosk mode?

---

### Post by Johnny B on 2010-02-21
you could try changing the permissions on passwd
chmod 744 /usr/bin/passwd

---

### Post by gmargo on 2010-02-22
See the **--mindays** option on **passwd**.  Set to a very large value.

---

### Post by mcduck on 2010-02-22
Just hide the configuration tools, lock the desktop settings and disable the terminal on that user account. While the users still are, in theory, able to change the password thy are unable to access any tool that they could use to actually do it.

Besides, you'll want to disable such features on any public-use computer anyway or you'll end spending quite alot time restoring the desktop settings after the users have messed them up. ;)

---

### Post by ubun_two on 2010-02-22
Thanks for the ideas, guys!  I'll look into them.

I am thinking about writing a script that resets the /home/guest/ directory, which (in theory) should reset everything every time the Ubuntu gets loaded (maybe using rsync?).  But I would still need the way to control the password changes.

---

