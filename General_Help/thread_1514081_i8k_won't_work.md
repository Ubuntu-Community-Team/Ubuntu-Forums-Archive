---
title: "i8k won't work"
date: 2010-06-20
forum: General Help
---

### Post by pi.theta on 2010-06-20
```
[theta@boolean-pc ~]$ sudo i8kfan
Password: 
can't open /proc/i8k: No such file or directory
```
```
[theta@boolean-pc ~]$ sudo modprobe i8k
FATAL: Error inserting i8k (/lib/modules/2.6.33-ARCH/kernel/drivers/char/i8k.ko): No such device
[theta@boolean-pc ~]$ 

```

I have a Dell Inspiron 1520. Recently it gets heated up quite a lot even after using cpufreq on *ondemand* mode. Sometimes the fan doesn't work. I use gnome on Arch Linux. I couldn't find any solution on the arch forums so I thought I could get some answers here. 

Regards,
Apoorv

---

### Post by wilee-nilee on 2010-06-20
Go to synaptic install gkrellm i8k use this link steps 2, 3, 4 then start gkrellm activate the plugin and adjust the fans a temp from gkrellm.
[http://ubuntuforums.org/showthread.php?p=5275415#post5275415](http://ubuntuforums.org/showthread.php?p=5275415#post5275415)

I always use this method I don't build a file with the temps set but set them in gkrellm, in other words you don't need step 5

---

### Post by TeoBigusGeekus on 2010-06-20
Try with [lm-sensors]("http://wiki.archlinux.org/index.php/Lm_sensors").

---

### Post by wilee-nilee on 2010-06-20
> **TeoBigusGeekus said:**
> Try with [lm-sensors]("http://wiki.archlinux.org/index.php/Lm_sensors").

If they follow my advice it will work I have a dell laptop and have used this method many times, and I am familiar with using the windows version of i8k. It's not a problem with the sensors

---

### Post by pi.theta on 2010-06-20
> **wilee-nilee said:**
> Go to synaptic install gkrellm i8k use this link steps 2, 3, 4 then start gkrellm activate the plugin and adjust the fans a temp from gkrellm.
[http://ubuntuforums.org/showthread.php?p=5275415#post5275415](http://ubuntuforums.org/showthread.php?p=5275415#post5275415)

I always use this method I don't build a file with the temps set but set them in gkrellm, in other words you don't need step 5

I got i8kfan working by using the force=1 option while loading the module. As  I understood gkrellm is just an gui interface to i8kmon. If I am wrong please correct me.

Regards,
Apoorv

---

### Post by wilee-nilee on 2010-06-20
> **pi.theta said:**
> I got i8kfan working by using the force=1 option while loading the module. As  I understood gkrellm is just an gui interface to i8kmon. If I am wrong please correct me.

Regards,
Apoorv

I think your correct that gkrellm is just a gui, personally I like to have hands on control of the fans. You can also set it to not be in the panel and on another desktop if you don't want to see it. It also can be shrunk to just the fans and temp by going through it and turning off functions you don't want to see. It is easy to manipulate if you know how. If put in startup applications with just the name gkrellm in the command it will turn on automatically when you boot the system. This is just how roll use what works for you.

---

