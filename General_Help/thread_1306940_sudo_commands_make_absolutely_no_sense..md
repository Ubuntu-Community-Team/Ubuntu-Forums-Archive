---
title: "sudo commands make absolutely no sense."
date: 2009-10-30
forum: General Help
---

### Post by Zer0 Suii on 2009-10-30
I've looked up all kinds of how-tos on this site and they all have some kind of
```

sudo something or another for 9000+ power
```Well, whenever I type ANY sudo command I get this:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package <insert package here>
```Can anyone explain what exactly sudo is? kthx.

I was mainly going for [this]("http://ubuntuforums.org/showthread.php?t=100169").

---

### Post by mechro on 2009-10-30
That thread is nearly 4 years old. The package mentioned in the opening post probably no longer exists.

Sudo is Ubuntu's way of giving a user permission to do root admin stuff...

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by alphaniner on 2009-10-30
sudo stands for 'super user do'.  It is a way to run commands that require root (root is the administrator or 'super user') powers.  It's not Ubuntu specific, but it is a core part of the Ubuntu design philosophy.  Or something like that.  In any case, in Linux most changes you make to the system require root power.

See [RootSudo]("https://help.ubuntu.com/community/RootSudo")

And if you post the FULL output of commands (including the command itself) you will be more likely to get help.  Just copy the everything from the terminal, and paste it here using code tags.

kthx

---

### Post by florus on 2009-10-30
sudo merely gives you authority to carry out commands which are otherwise restricted. It lets you temporarily operate as root.

---

### Post by mechro on 2009-10-30
If you're looking for all the desktop cubey eye candy then some of it is already installed in Ubuntu: **System>Preferences>Appearance>Visual Effects**.
If you want to configure this stuff then install **Advanced Desktop Effects Settings (ccsm)** from **Applications>Add/Remove**.

---

### Post by todak on 2009-10-30
> **mechro said:**
> If you're looking for all the desktop cubey eye candy then some of it is already installed in Ubuntu: **System>Preferences>Appearance>Visual Effects**.
If you want to configure this stuff then install **Advanced Desktop Effects Settings (ccsm)** from **Applications>Add/Remove**.

Wrong thread, maybe?

---

### Post by Zer0 Suii on 2009-10-30
> **mechro said:**
> If you're looking for all the desktop cubey eye candy then some of it is already installed in Ubuntu: **System>Preferences>Appearance>Visual Effects**.
If you want to configure this stuff then install **Advanced Desktop Effects Settings (ccsm)** from **Applications>Add/Remove**.
Wow! Thanks! That worked! I'm watching the rain effect right now. It's awesome!

---

### Post by mechro on 2009-10-30
> **todak said:**
> Wrong thread, maybe?

Nope. As well as the sudo query, Zer0 Suii said "I was mainly going for [[COLOR="red"]this[/COLOR].](http://ubuntuforums.org/showthread.php?t=100169)"

---

### Post by todak on 2009-10-30
> **mechro said:**
> Nope. As well as the sudo query, Zer0 Suii said "I was mainly going for [[COLOR="red"]this[/COLOR].](http://ubuntuforums.org/showthread.php?t=100169)"

Whoops, apologies. I caught that just as I posted my response. Sorry! :oops: :D

---

### Post by mechro on 2009-10-30
> **todak said:**
> Whoops, apologies. I caught that just as I posted my response. Sorry! :oops: :D

No probs. :D

A satisfied O.P. and an apology! What more could I ask for? :D

---

