---
title: "no names in chroot environment"
date: 2010-12-04
forum: General Help
---

### Post by c2tarun on 2010-12-04
hi friends
i created a chroot environment for lucid.
when i log in by executing this command
"sudo chroot /var/chroot/lucid"
it logged me in as a root user.
i created a new account there, when i log in by that account i cant see anything written before $ sign. even if i change directory or anything else i cant see anything.
any solution??

---

### Post by efflandt on 2010-12-04
Anything you want to access in your chroot typically has to be **within your chroot**.  So when you create a user within chroot, it depends what is in /etc/profile, /etc/bash.bashrc, and /etc/skel/.profile or .bashrc within the chroot when you create that user, or what .profile or .bashrc that user adds to their chroot home, and whether any of those sets **PS1**.

```
efflandt@natty-ssd:~$ echo $PS1
\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$
```See ~/.bashrc while a normal user before you chroot.

---

