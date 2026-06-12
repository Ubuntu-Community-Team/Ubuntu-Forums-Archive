---
title: "root account enabled"
date: 2009-07-20
forum: General Help
---

### Post by philcamlin on 2009-07-20
ok like a month ago i was told while installing something to enable root 

sudo su

but ive been reading my comp is really vulnerable now 

how can i fix this or is this even an issue ?

thanks:D

---

### Post by credobyte on 2009-07-20
```
sudo passwd -l root
```

---

### Post by philcamlin on 2009-07-20
> **credobyte said:**
> ```
sudo passwd -l root
```

thanks

---

### Post by Trebaruna on 2009-07-20
sudo su makes your current session root. It does not permanently enable the root account. If you can login as root then the account is active.

Even when it is active, if you have a good password protecting it there is no real problem. That is, if you don't use that account for your day to day work...

---

### Post by philcamlin on 2009-07-20
how do i chsange the root pswd 

cause its not very hard :(

---

### Post by jenkinbr on 2009-07-20
> **philcamlin said:**
> how do i chsange the root pswd 

cause its not very hard :(
That subject goes against the security model of ubuntu, and thusly cannot be posted here.  If you want to do this, you will need to find out elsewhere (i.e. google)

Sorry.

---

### Post by credobyte on 2009-07-20
> **philcamlin said:**
> how do i chsange the root pswd 

cause its not very hard :(

You started with "how to disable root password" and ended up with "how do I change it" ? What I'm missing here ?
If you need to do something as root, use [COLOR=RoyalBlue]sudo -i [/COLOR]!

---

### Post by CatKiller on 2009-07-20
> **philcamlin said:**
> how do i chsange the root pswd 

If you've only used **sudo su**, then you haven't enabled a root password at all. If you've run something else to enable a root password then the **passwd** command that credobyte gave you will lock it again.

That will generally be sufficient.

If you are concerned that users of your computer will be able to guess your user password and so use that to gain unauthorised access to your privileges using sudo, you can change your password to something stronger through the Users and Groups tool, or with ```
passwd <username>
```from the Terminal. You can start reading about password strength [here]("http://en.wikipedia.org/wiki/Password_strength").

---

### Post by philcamlin on 2009-07-21
> **CatKiller said:**
> If you've only used **sudo su**, then you haven't enabled a root password at all. If you've run something else to enable a root password then the **passwd** command that credobyte gave you will lock it again.

That will generally be sufficient.

If you are concerned that users of your computer will be able to guess your user password and so use that to gain unauthorised access to your privileges using sudo, you can change your password to something stronger through the Users and Groups tool, or with ```
passwd <username>
```from the Terminal. You can start reading about password strength [here]("http://en.wikipedia.org/wiki/Password_strength").

thanks that was useful :)

---

