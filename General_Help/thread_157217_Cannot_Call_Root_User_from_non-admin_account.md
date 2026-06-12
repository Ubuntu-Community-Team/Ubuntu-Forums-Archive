---
title: "Cannot Call Root User from non-admin account"
date: 2006-04-08
forum: General Help
---

### Post by cgborkgb on 2006-04-08
Hi.  I was wondering if there is a way to give a non-admin user the ability to call for the root user to execute administrative commands (like updating via synaptic).  I was told once to do the following:

Edit /etc/group and add the new user account to the admin line. This is a comma separated list so you can add more than one:

```
admin:x:106:user1,user2, ...,usern
```

but that actually gives the new user administrative priveleges instead of allowing the user to call the root user.  Perhaps I am confused a bit by the installation.  I am prompted to create a user that has full priveleges.  Then if I create a new user without admin priveleges, the new user cannot call for admin priveleges from the initial account (root acct?) by typing su or sudo in the command line.  This will work in SuSE.  I'm sure there is a better way to update my computer than by switching users ](*,) 

thanks for reading :)

---

### Post by limaunion on 2006-04-08
Why don't you add the user you want with the command 'visudo' to the sudoers file ? I suggest you to read the following: [http://help.ubuntu.com/starterguide/C/ch06.html#whatissudo](http://help.ubuntu.com/starterguide/C/ch06.html#whatissudo)

HTH.

---

