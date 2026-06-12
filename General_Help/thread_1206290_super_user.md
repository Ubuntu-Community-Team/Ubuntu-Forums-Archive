---
title: "super user?"
date: 2009-07-07
forum: General Help
---

### Post by jhapk on 2009-07-07
Hi,

when I run a command using "sudo", Ubuntu asks me for a password and it works fine.
But when I simply type $su to login as super user, it asks me for the password and when I enter the same password and it shows 

```
su: Authentication failure
```Any reasons?

---

### Post by rossmoore on 2009-07-07
My limited understanding is that su requests to be superuser. That'll fail 'cos you don't have authority.
You'd need "sudo su" to go superuser.
I think there's a preferred method if you want to be superuser for a while, something like "sudo -s" or something?

---

### Post by jpeddicord on 2009-07-07
> **rossmoore said:**
> My limited understanding is that su requests to be superuser. That'll fail 'cos you don't have authority.
You'd need "sudo su" to go superuser.
I think there's a preferred method if you want to be superuser for a while, something like "sudo -s" or something?

sudo -i would probably be the right way to go about it, as it drops your own environment and gives you a fresh shell.

And to those ready to fire off an "enable the root account" post - don't. :)

---

### Post by jhapk on 2009-07-07
Thanks

Both "$sudo su" and "$sudo -i" work fine.

---

### Post by kpkeerthi on 2009-07-07
> **jhapk said:**
> Hi,

when I run a command using "sudo", Ubuntu asks me for a password and it works fine.
But when I simply type $su to login as super user, it asks me for the password and when I enter the same password and it shows 

```
su: Authentication failure
```Any reasons?

This will work if you enable 'root' account.

---

### Post by jpeddicord on 2009-07-07
> **kpkeerthi said:**
> This will work if you enable 'root' account.

Really, I wasn't kidding.

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by kpkeerthi on 2009-07-07
> **jacobmp92 said:**
> Really, I wasn't kidding.

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
You're right. I don't have nor do I recommend enabling the root account.

---

