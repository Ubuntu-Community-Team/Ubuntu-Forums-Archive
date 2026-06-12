---
title: "I broke my system by taking ownership of the root directory. Help needed."
date: 2011-11-08
forum: General Help
---

### Post by kshivamaurya on 2011-11-08
i have root account activated.i have taken ownership of / directory(root) as shivam and group shivam.how to undo this.i am unable to use graphical login.(ubuntu 11.10).violet screen still appears

---

### Post by Dangertux on 2011-11-08
Did you chown / ? Is that what you mean by take ownership or are you just logged in as root. 

If you just logged in as root, log out and log in as a normal user

The documentation here can help you disable your root account again : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bodhi.zazen on 2011-11-08
> **kshivamaurya said:**
> i have root account activated.i have taken ownership of / directory(root) as shivam and group shivam.how to undo this.i am unable to use graphical login.(ubuntu 11.10).violet screen still appears

Moved to general help.

This is not a security thread nor is it a "serious security flaw", it is you running as root (which is not advised) and making changes to your system without understanding what you are doing.

You will need to boot a live CD, mount your root partition, and chown / back to root.

```
mount /dev/sda1 /mnt #chande "sda1" to your ubuntu partition
chown root.root /mnt
```

If that fails you can try to boot to recovery mode , but it may fail as ownership of / is off, and in that case you will need to re-install.

Please read the rootsudo link you were given and do some reading before you go editing or changing ownership of system files.

---

### Post by philinux on 2011-11-08
> **kshivamaurya said:**
> i have root account activated.i have taken ownership of / directory(root) as shivam and group shivam.how to undo this.i am unable to use graphical login.(ubuntu 11.10).violet screen still appears

Thread title changed.

---

### Post by bwanamarko on 2011-12-13
> **kshivamaurya said:**
> i have root account activated.i have taken ownership of / directory(root) as shivam and group shivam.how to undo this.i am unable to use graphical login.(ubuntu 11.10).violet screen still appears
I broke my system too, typing random combinations su <commands>, su <username> commands, sudo <commands> (I was trying to share a folder). I should have read the man files too, but luckily Oneiric Ocelot fixed itself using recovery mode, still did not know what I was doing. Nearly 4th time reinstalling, but this time too many files on disk.

---

