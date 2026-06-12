---
title: "vbox error"
date: 2009-08-09
forum: General Help
---

### Post by madinc on 2009-08-09
i need to disable the kvm kernel extension and recompile the kernel,
some help please?

---

### Post by coldReactive on 2009-08-09
Well, you can recompile this way:

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by madinc on 2009-08-09
thanks that works but i need to disable the kvm kernel extension first, any ideas please?
i did try reactos 0.3.7 but i was using windows xp at the time.

---

### Post by coldReactive on 2009-08-09
[http://ubuntuforums.org/showthread.php?t=766463](http://ubuntuforums.org/showthread.php?t=766463)

---

### Post by madinc on 2009-08-09
gee thanks man it works all good now thanks for the linkyou the man.

you can stop kvm doing:sudo /etc/init.d/kvm stop

or you can remove it wich was better for me, removing kvm is pretty easy:

$ sudo apt-get purge kvm

This will unload the kvm modules, remove the kvm and purge its configuration (for example, files in /etc).

If kvm was already removed, the following will finally purge it:

$ sudo dpkg -P kvm


i will now download the new reactos and try it thanks again.

---

### Post by coldReactive on 2009-08-09
> **madinc said:**
> i will now download the new reactos and try it thanks again.

Just so you're aware, it's in my signature, not a part of the post.

---

### Post by madinc on 2009-08-09
> **coldReactive said:**
> Just so you're aware, it's in my signature, not a part of the post.

sorry but i don't understand .

---

