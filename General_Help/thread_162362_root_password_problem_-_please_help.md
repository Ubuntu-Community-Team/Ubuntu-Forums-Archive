---
title: "root password problem - please help"
date: 2006-04-18
forum: General Help
---

### Post by amirjpl on 2006-04-18
hello, 

the way i used to login as administrator in suse linux was just typing:
su

and then type in my password. and i would be logged in as an administrator.

in ubuntu installation it never asked me to set my root password. so i have no idea what my root password is. is it like this for everyone or is it just me.

please post any solutions or questions that you might have.

---

### Post by aysiu on 2006-04-18
https//wiki.ubuntu.com/RootSudo
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by mbailey on 2006-04-18
Ubuntu is set up to reduce/eliminate the need to use the root account directly. You are expected to use sudo instead. Whatever initial account you built the system with will have sudo privilege and the idea is that you will never need more rights.

However, my first action after install was to set the root password. System->administration->users and groups shows you your users and  if you check the all users check box you can reset the root password.

Having said that, sudo is more secure, logged and if root cannot log in remotely, defends against dictionary attacks. I set myself up with root, but don't really need it - be sure you actually do before you give up on the default settings

Martin

---

