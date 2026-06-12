---
title: "who can use sudo?"
date: 2006-03-10
forum: General Help
---

### Post by m.musashi on 2006-03-10
As the person who set up ubuntu, I know I can do admin tasks via sudo. However, if I'm currently logged in under a different user (wife, kid) and I want to do something requireing admin rights, how do I do that? I tried sudo but my password doesn't work and neither does the password of the current user.

Am I doing something wrong?

---

### Post by Zelut on 2006-03-10
Two solutions for this:

You could add these other users to the allowed 'sudo'ers list (sudo visudo)
create a listing under root ALL=(ALL) ALL.. or whatever

set the root password (sudo passwd root)
and then 'su' from one of their accounts.  That will change you to root (anyone with the root password can do it) and you'll be able to administrate from any account.

---

### Post by hscottyh on 2006-03-10
the person logged in has to belong to the 'sudo' group.

You probably give those privaledges to your child. So you could switch user to the origanal account in a terminal and the sudo. Here is an example:

From a terminal:
su xxxxxx      - where xxxxxx is the user you want to switch to.
it will ask for a password enter that then you are ready to sudo.

---

### Post by m.musashi on 2006-03-10
Cool. Thanks. I thought I understood this but I've tried to administrate from another account until now and it didn't work.

---

### Post by taurus on 2006-03-10
You need to add that person to group "adm" in /etc/group!

---

### Post by redactech on 2006-03-10
Don't need to do change anything

olivier@portablelinux2:/home/david$ su david (david being the admin of the machine)
Password: (type the admin pwd)
david@portablelinux2:~$

you're in

---

