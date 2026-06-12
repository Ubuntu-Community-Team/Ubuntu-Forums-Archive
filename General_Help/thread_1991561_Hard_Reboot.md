---
title: "Hard Reboot"
date: 2012-05-30
forum: General Help
---

### Post by Ubun2to on 2012-05-30
Today, I went to shutdown, and left, and the computer decided to hang on the shutdown screen.
I was forced to do a hard reboot via the power button.
I know you shouldn't do that, but I had to. What should I do to make sure I didn't screw anything up?

---

### Post by kanikilu on 2012-05-30
My computer just suffered an unclean shutdown today (power failure), but it seems to be pretty resilient. If you want to force a filesystem check on the root partition, though, just do:

```
sudo touch /forcefsck; sudo reboot
```

---

### Post by oldfred on 2012-05-30
Think of the elephants before a hard shutdown.

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by Ubun2to on 2012-05-31
> **oldfred said:**
> Think of the elephants before a hard shutdown.

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

I tried that and waited 15 minutes. I also tried ALT + SysRq + K.

---

### Post by Ubun2to on 2012-05-31
> **kanikilu said:**
> My computer just suffered an unclean shutdown today (power failure), but it seems to be pretty resilient. If you want to force a filesystem check on the root partition, though, just do:

```
sudo touch /forcefsck; sudo reboot
```
This gives me:
```
myname is not in the sudoers file. This incident will be reported.
```

---

### Post by melrokz on 2012-05-31
> **Ubun2to said:**
> This gives me:
```
myname is not in the sudoers file. This incident will be reported.
```

This can happen if you are not an 'administrator' user. See 'User Accounts'.

If you are not, you need to add yourself to the 'admin' group.

1. User Accounts > click your name > Account Type > change.
2. sudo adduser myname admin
   (and give password of an admin user :( )
3. get into "recovery mode" and login as root, then do:
   sudo adduser myname admin

---

### Post by jmore9 on 2012-05-31
" myname is not in the sudoers file. This incident will be reported "

So if you are the only user on the machine , who is the machine going to report you to ?

My buddies and myself have always wondered about that .

---

### Post by melrokz on 2012-05-31
> **jmore9 said:**
> " myname is not in the sudoers file. This incident will be reported "

So if you are the only user on the machine , who is the machine going to report you to ?

My buddies and myself have always wondered about that .

That's silly, I too laughed at that. Not the cops anyway :lolflag:

---

