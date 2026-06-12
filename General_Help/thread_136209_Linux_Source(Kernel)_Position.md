---
title: "Linux Source(Kernel) Position"
date: 2006-02-25
forum: General Help
---

### Post by dJnEvS on 2006-02-25
not sure how to call it... but i try to install SynCE, and i need to install some wierd drivers i guess
but where i run Make of the driver thing, it says that it cant find the linux source or something, i i've looked into the Make file, and it's looking for /usr/src/Linux-x.x.x whatever so it cant find it..
but, where CAN i find it?

---

### Post by thomashauk on 2006-02-25
Search for linux-source in synaptic or

```
sudo aptget install linux-source-2.6.12
```

---

### Post by az on 2006-02-25
No.  Install the linux-headers package for your kernel.

Install linux-headers-386 if you are running the default kernel.

It is a lot more complicated to download the whole source, configure it to match your kernel.  Just use the linux-headers.  That is what they are for!

---

### Post by Trab on 2006-02-25
i just wrote a HowTo on Synce, it should appear in the customization section soon... i hope...

---

### Post by dJnEvS on 2006-03-06
[Help?](http://www.ubuntuforums.org/showthread.php?t=136257)

---

### Post by dJnEvS on 2006-03-06
bump!

---

