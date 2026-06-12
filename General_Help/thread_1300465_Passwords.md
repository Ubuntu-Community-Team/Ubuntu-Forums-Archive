---
title: "Passwords"
date: 2009-10-25
forum: General Help
---

### Post by chugeniv on 2009-10-25
Hi,

When I recently installed toe latest Ubuntu software, I sort of just followed instructions as presented (did the same with earlier version as well).

Since my desktop is used exclusively at home and I am the only user, was it really necessary for me to set up a user/password login? As well as have a password for admin?

It would speed up my login in if I could get rid of the need for passwords. How do I get rid of them if not needed?

Thanks for your help,
Bob

---

### Post by psycho5 on 2009-10-25
You can go to System> Admin > Login Window and enable automatic log in for your username. That should speed up the login process.

It's a really good idea to keep the admin password. You can't go wrong with security.

---

### Post by MelDJ on 2009-10-25
edit, misread

---

### Post by DeMus on 2009-10-25
> **chugeniv said:**
> Hi,

When I recently installed toe latest Ubuntu software, I sort of just followed instructions as presented (did the same with earlier version as well).

Since my desktop is used exclusively at home and I am the only user, was it really necessary for me to set up a user/password login? As well as have a password for admin?

It would speed up my login in if I could get rid of the need for passwords. How do I get rid of them if not needed?

Thanks for your help,
Bob

It is always a good idea to have a password, especially for root (admin). This password btw is your own personal password, there is no extra root password.
You can however log in automatically without having to type your password when the pc boots:
```
Go to System -> Administration Login Window
```
```
Choose TAB Security (the name indicates it is important)
```
```
Set the first thick box Enable Automatic login and choose your name.
```
```
Don't change the other items.
```

Whenever you need to do something root has to do for you, you have to type the password. Just get used to it. This is not often when you just use your computer the normal way.
The system with root and a root password is for your own safety: when root is active you can destroy the complete system. So be careful.

---

