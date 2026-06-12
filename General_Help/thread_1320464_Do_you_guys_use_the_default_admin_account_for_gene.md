---
title: "Do you guys use the default admin account for general use?"
date: 2009-11-09
forum: General Help
---

### Post by viking_maniac on 2009-11-09
I'm just wondering what account and security policies you guys have.

Do you use the shipped admin account for general use, or do you create a new account with restricted permissions that you log into instead?

---

### Post by Giblet5 on 2009-11-09
I use an admin account with reduced restrictions.

I do not recommend doing this.

I set up restricted accounts for the kids so they can play Unreal Tournament 2004 and kill each other without hosing up my system.

---

### Post by sh4d0w808 on 2009-11-09
No and not recommended.

Admin account present only for admin tasks.

---

### Post by alphaniner on 2009-11-09
What do you mean by the shipped admin account?  The user created during installation?  Or root?  I use the former.  At home with all default settings, at work with NOPASSWD set for sudo.

---

### Post by 3rdalbum on 2009-11-09
I use the first user account created, which can *sudo* to root when necessary. Default security configuration of Ubuntu.

---

### Post by blueridgedog on 2009-11-09
> **viking_maniac said:**
> 
Do you use the shipped admin account for general use?

This would be the user account called "root" and no, it is not intended for general use.  The account made during the install has the right to run commands as this account via the "sudo" command.  Other users (kids, family) may or may not have this right (more than likely not).  The real admin account therefore is the user account made during the install.

---

### Post by viking_maniac on 2009-11-11
I'm not talking about the root account. I'm talking about the default account that you create and log into the first time when you install the system, where you use *sudo* to do root tasks.

Do you use this account for default use, or do you create a new one with less privileges?

---

### Post by marcopolo1981 on 2009-11-11
I use the default (the one set up at install) and sudo su in terminal when I need elevated control of my system. There isn't any other accounts on my pc as I am the only user.

---

### Post by Commander_Keen on 2009-11-11
I too use the default account.

---

### Post by ensign.dan on 2009-11-11
The same here.  I use standard (first account created) for everyday use, but if you are connecting your system for example by ssh from outside you may want to add another user.

---

### Post by Iowan on 2009-11-11
Default - it's already a "normal user" unless "super-sized" via **sudo**. One a previous version of my server, I built a "pseudo-root" user... but discovered that **sudo** did essentially the same thing.

---

### Post by wojox on 2009-11-11
Admin account.

---

### Post by blueridgedog on 2009-11-11
In that case, yes, I use an admin account with sudo capacity.

---

### Post by lykwydchykyn on 2009-11-11
Since I came to Ubuntu from other Linux distros where everyone had access to su to root (provided they knew root's password), it didn't seem like a big deal to me to use an account with sudo access for daily use.

I guess one more level of protection might make some feel better; seems overkill to me.

My kids, on the other hand, get non-admin accounts. ;)

---

