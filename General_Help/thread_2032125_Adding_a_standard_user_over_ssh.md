---
title: "Adding a standard user over ssh"
date: 2012-07-23
forum: General Help
---

### Post by foxy123 on 2012-07-23
I have to add a standard user on a remote desktop using ssh on my phone. If I just do 
```
adduser <username>
```will it be a standard user (I mean able to print, use teh Internet etc) or I have to edit privileges in some way?

---

### Post by elliotbeken on 2012-07-23
This user will be a normal user, as in they will not be able to run sudo commands.

If you would like to allow them to use sudo commands run:

sudo gpasswd -a foxy123 admin

(where foxy123 is the username of the new user and admin is the sudo group)

---

### Post by foxy123 on 2012-07-23
> **elliotbeken said:**
> This user will be a normal user, as in they will not be able to run sudo commands.

If you would like to allow them to use sudo commands run:

sudo gpasswd -a foxy123 admin

(where foxy123 is the username of the new user and admin is the sudo group)


Thanks a lot.

---

### Post by Morbius1 on 2012-07-23
> **elliotbeken said:**
> sudo gpasswd -a foxy123 admin
Just so you know - in 12.04 there is no admin group. It's now sudo:
```
sudo gpasswd -a foxy123 sudo
```

---

### Post by foxy123 on 2012-07-24
Thanks again. 

Is it possible to launch the Unity desktop over ssh? I need to configure launchers.

---

