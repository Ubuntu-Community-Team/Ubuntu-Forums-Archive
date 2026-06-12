---
title: "No Init found Try passing init =bootarg"
date: 2010-10-01
forum: General Help
---

### Post by mnconny on 2010-10-01
I have installed Ubuntu 10.04 .. normally and I installed also some programs; I had problems with the monitor and many times I shutted down the CPU when I changed the monitor and turned on angain and  appears a black screen:

after

mount: mounting /dev on root/dev failed: no such such file or dir
mount: mounting /sys on root/sys failed: no such such file or dir
mount: mounting /proc on root/proc failed: no such such file or dir

Target filesystem doesnt have /sbin/init
no init found. Try passing init=bootarg

Busybox v1.13 .3 -1ubuntu11  built in shell (ash)
Enter help for a lis of built-in commands


(initramfs) 

I dont know what to do. I was looking for in internet and nothing helped me.

Can I do something with out format again?

Thanks for the help

---

### Post by andrewthomas on 2010-10-01
post the output of 

```
sudo fdisk -l
```

COPY and PASTE the command in the terminal

---

### Post by mnconny on 2010-10-01
Is not possible enter that command sudo 

(initramfs)_   just accept some commands which appear typing ^help^

---

### Post by andrewthomas on 2010-10-01
Do you have a LiveCD?

Is it a regular install or using wubi?

---

### Post by mnconny on 2010-10-01
I  tryed with livecd but I dont know what is wrong 

"appear a blackscreen with  Strike F1 to retry boot, F2 for setup utility "


regards 

mnconny

---

