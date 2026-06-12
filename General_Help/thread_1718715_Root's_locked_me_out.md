---
title: "Root's locked me out"
date: 2011-03-31
forum: General Help
---

### Post by dramspringfeald on 2011-03-31
I'm having a hard time getting into my root files. every time I try I am denied when installing software updating anything.

I'm using 10.04 LTS any help would be useful.

---

### Post by dabl on 2011-03-31
> **dramspringfeald said:**
> I'm having a hard time getting into my root files. 

What do you mean by this?  You don't "get into" any files when you install or update your packages.  Tell more about what you are trying to do, and how you are trying to do it.

---

### Post by bodhi.zazen on 2011-03-31
sudo for commands
gksu for graphical applications

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Enter your user's password when asked.

If you are locked out of sudo, then you will need to fix your problem from recovery mode or a live CD. Typical problems are :

1. You are not in the admin group.
2. You changed your hostname. Your hostname needs to be the same in /etc/hosts and /etc/hostname

---

### Post by dramspringfeald on 2011-03-31
Well I'm still new to root and I'm trying to update files as well as install files from the software center. however every time I try to I get denied because I am not root. so I was wondering how do I get those privileges? 

I am also trying to move files from my laptop (this system) to my desktop that hs no Internet (no net at my place) so I'm trying to manually update the files for my art programs and the like. like I use to with windows (program files)

again still newb but any help would be useful.

---

### Post by bodhi.zazen on 2011-03-31
> **dramspringfeald said:**
> Well I'm still new to root and I'm trying to update files as well as install files from the software center. however every time I try to I get denied because I am not root. so I was wondering how do I get those privileges? 

I am also trying to move files from my laptop (this system) to my desktop that hs no Internet (no net at my place) so I'm trying to manually update the files for my art programs and the like. like I use to with windows (program files)

again still newb but any help would be useful.

What part of sudo / gksu did you not understand ?
What part of the link I gave you did you not understand ?

```
gksu nautilus --no-desktop
```

When asked for a password, enter your login password.

---

### Post by dramspringfeald on 2011-04-09
> **bodhi.zazen said:**
> What part of sudo / gksu did you not understand ?
What part of the link I gave you did you not understand ?

```
gksu nautilus --no-desktop
```When asked for a password, enter your login password.


Thanks I got that. Still what part of I wasn't just talking to you. the majority of the reply was for dabl.

---

