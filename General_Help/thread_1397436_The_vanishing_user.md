---
title: "The vanishing user?"
date: 2010-02-03
forum: General Help
---

### Post by ashryalls on 2010-02-03
I'm running 9.10 64 bit, with little to no issues up to this point.  However last night the need arose to add a new user.  Before doing this my existing user showed in the list of users for login allowing me to simply click and enter my password.  It also showed in users and groups.  

Upon adding the new user this is no longer the case (for my old user and new).  It does not appear in the login list (ie no users now show and I have to manually type the username) and both users now no longer show in users and groups, the only user there is root (unless I change the show all users option in /apps/gnome-system-tools/users/ through gconf editor)

Any help would be appreciated as I'm gradually pulling more hair out over this.  
Thanks,
Ash

---

### Post by bluefrog on 2010-02-03
what are the uid of your users?

id user
uid=?

9.10 will not show uid < 1000

---

### Post by ashryalls on 2010-02-03
Well I've since deleted the second user for the time being, however the UID of my original user is 1000.

---

### Post by grendel38 on 2010-02-03
I have assigned a user a UID of 501 (to simplify file sharing with a mac)

Is there any way to make this user show up in the gdm login screen?

---

### Post by ashryalls on 2010-02-03
Just to add to this, I've reinstalled the gdm package and that has made no difference.  Anyone any ideas?

---

### Post by ashryalls on 2010-02-12
Does no one have any ideas on this?

---

### Post by polki@mac.com on 2010-02-15
Users with a UID less than 1000 doesn't show up at login. As to why, I don't know...

---

### Post by rnerwein on 2010-02-15
hi
i didn't try it by myself - but ther are two config files:
/etc/login.con and /etc/adduser.conf and in both you can find: UID_MIN 1000
may be login is looking in this file ?????

ciao

---

