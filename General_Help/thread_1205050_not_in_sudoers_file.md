---
title: "not in sudoers file"
date: 2009-07-05
forum: General Help
---

### Post by reggler on 2009-07-05
Hi There,

I got an emergancy kinda sirtuation and i don't know howi got there :o
I have a ubuntu install with one user account 'reg' and when i try to sudo i get "reg is not in the sudoers file". So how can i fix this as I can't do anything really, can I? I assume I'll need to boot from a CD, edit the /etc/sudoers file or something, any one a clue? I'm not able to login as root either :o

Thanks 1000!

PS: I tried to scp the /etc/sudoers from my other machine but i'm not able to login as root :(

---

### Post by taurus on 2009-07-05
Basically, you boot your machine to recovery mode from GRUB menu.  Then, you add yourself, your username, to group admin and that should do it.

Are you the original user that you created when you installed Ubuntu?

---

### Post by michy99 on 2009-07-05
Make sure you use visudo to edit the sudoers file. It is the only safe way to do it.

---

### Post by reggler on 2009-07-05
> **taurus said:**
> Basically, you boot your machine to recovery mode from GRUB menu.  Then, you add yourself, your username, to group admin and that should do it.
How do I add myself (?) and my username (reg) to the group admin?
> **taurus said:**
> 
Are you the original user that you created when you installed Ubuntu?
Yes I am.

---

### Post by taurus on 2009-07-05
One way is to add reg to group admin in /etc/group after booting from the recovery mode.

```
nano -B /etc/group
```

---

### Post by reggler on 2009-07-05
> **taurus said:**
> One way is to add reg to group admin in /etc/group after booting from the recovery mode.

```
nano -B /etc/group
```

Awesome, thanks man - I see there's a group 'sudo' what is this for then or better: what else does 'admin' include?

---

