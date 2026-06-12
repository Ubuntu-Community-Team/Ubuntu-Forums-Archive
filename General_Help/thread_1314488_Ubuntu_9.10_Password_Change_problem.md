---
title: "Ubuntu 9.10 Password Change problem"
date: 2009-11-04
forum: General Help
---

### Post by terabyte1 on 2009-11-04
On making a clean install of Ubuntu 9.10 I attempted to change the password to a more secure one. After ten attempts on trying to change it various ways i've given up. Ubuntu refuses to change the password and in one instance, refused both the 'old' password and the newly suggested one, thereby locking me out of my own computer! I've never had this before ...please advise? :mad:

---

### Post by sisco311 on 2009-11-04
Reset your password from the *Recovery Mode.*

[http://psychocats.net/ubuntu/resetpassword]("http://psychocats.net/ubuntu/resetpassword")

---

### Post by P4man on 2009-11-04
Make sure you are not confusing your account password (to log in and what you need for sudo) and your keyring password (what you need to open the keyring so apps like network manager, email and instant messengers can retrieve your password. by default they are the same but if you change your account password, the keyring password is not changed.

Anyway to change your account password, boot ubuntu in recovery mode, select a root shell and type

```
passwd yourusername

reboot
```
To change your keyring password,  log in to your account
Applications -> Accessories-> Passwords

Rightclick Passwords and  select change password. If you make it the same as your account password, the keyring will be unlocked automatically when you login.

---

