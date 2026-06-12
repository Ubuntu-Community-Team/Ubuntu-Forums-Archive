---
title: "installing packages?"
date: 2009-11-30
forum: General Help
---

### Post by othiena on 2009-11-30
Is it possible to build and install packages while booting from the live CD onto the hard drive of a basic command line system?

If so how?

---

### Post by sanemanmad on 2009-11-30
So you want to update / install packages on a HDD already running linux via the live cd?

If so, any particular reason it must be done this way?

---

### Post by othiena on 2009-11-30
I want to install Enlightenment and the Entrance (display manager) without having gnome or kde on the harddrive. It is only 10 gb and for me every mb counts.

---

### Post by Cheesemill on 2009-11-30
Yes you can. You need to mount the root partition of the system you wish to install into and then run the chroot (**ch**ange **root**) command with the appropriate switches (see *man chroot* for more details). This way you can install packages into a non-running system.

EDIT - Just had a look at *man chroot* and it's a pretty useless description. Basically if you mount your other system partition as /mnt/otherroot you just need to do:
```
chroot /mnt/otherroot
```

---

### Post by othiena on 2009-11-30
I probably should of mentiond that i am not vary comfortable with the command line.

---

### Post by syeef on 2009-11-30
Yes.. possible. follow the instruction below

1)Boot from the live CD
2)Connected to Internet
3)Install the software you want
4)go to   **/var/cache/apt/archives** folder and copy all *.deb file in your hard drive.

---

