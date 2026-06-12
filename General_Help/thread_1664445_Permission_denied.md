---
title: "Permission denied"
date: 2011-01-11
forum: General Help
---

### Post by neokyle on 2011-01-11
I cant do anything with the user i created, i try to run a script i get permission denied. It wont let me mount, or install things.

How can i give the user i created access to everything root can do.

thanks

---

### Post by cipherboy_loc on 2011-01-11
Use sudo:

```
sudo mount [options]
```

Run:

```
man sudo
```

For more help.

---

### Post by neokyle on 2011-01-11
It says i am not in the sudoers file. This incident will be reported.

---

### Post by cipherboy_loc on 2011-01-11
Do you have any other users? Log in as your admin user (the one you created whenyou installed Ubuntu) and add the user to the admin group (I think). Google: Ubuntu sudo access.



Cipherboy

---

### Post by neokyle on 2011-01-11
> **cipherboy_loc said:**
> Do you have any other users? Log in as your admin user (the one you created whenyou installed Ubuntu) and add the user to the admin group (I think). Google: Ubuntu sudo access.



Cipherboy

I was actually able to do visudo and add my user to suduers list. 

now i can do sudo from that user.

thank you for the help :)

---

