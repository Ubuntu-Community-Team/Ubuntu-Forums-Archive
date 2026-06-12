---
title: "how to make ubuntu 11.10 64bit further leverage large memoy"
date: 2012-01-21
forum: General Help
---

### Post by ilovelyy on 2012-01-21
Hi there,
are there any optimizations I can do to further utilize large memory. I have 8 G memory on my laptop and I installed ubuntu 11.10 64bit. I Now the system only use 10% of my memory.

Thank you.

---

### Post by kazztan0325 on 2012-01-21
What about running more than one Virtual Machine?

---

### Post by ilovelyy on 2012-01-21
> **kazztan0325 said:**
> What about running more than one Virtual Machine?

I don't use virtual machine. I just want system to cache more data so I can launch application faster. I want minimize disk write.

---

### Post by kazztan0325 on 2012-01-21
Then what about using Ramdisk?

You would be able to refer this post and its thread.
**"HOW TO: mount /tmp to ram for increased preformance."**
[http://ubuntuforums.org/showthread.php?t=1054129]("http://ubuntuforums.org/showthread.php?t=1054129")

---

### Post by dino99 on 2012-01-21
you can tweak the swappiness if you like, but the default settings are already optimized

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by snowpine on 2012-01-21
> **ilovelyy said:**
> I don't use virtual machine. I just want system to cache more data so I can launch application faster. I want minimize disk write.

Launching applications does not write to disk (it reads).

---

### Post by xyzzyman on 2012-01-21
You could install preload

```
sudo apt-get install preload
```

Slows down initial boot a tad for some people, but it preloads apps as it learns what you use. Depending on the speed of your system you may see a difference. If not you just have more ram than you need. I have 4GB's and even when I run a VM I never use all my RAM let alone touch swap. Even compiling a kernel I don't go over 4GB's.

---

### Post by snowpine on 2012-01-21
Loading an application takes x seconds. If you use preload then you shunt those x seconds to the boot process rather than while you are using the desktop. There is no change in x but perhaps a psychological benefit (a small increase in boot time is less frustrating than a laggy desktop).

---

### Post by Bobhuber on 2012-01-21
Decrease your swappiness to 10. I don't think you will see any difference in memory usage but you should  see a vast improvement in performance. Make sure you read the whole page (it's on the bottom).
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by xyzzyman on 2012-01-21
> **snowpine said:**
> Loading an application takes x seconds. If you use preload then you shunt those x seconds to the boot process rather than while you are using the desktop. There is no change in x but perhaps a psychological benefit (a small increase in boot time is less frustrating than a laggy desktop).

preload runs all the time. it reanalyzes every 20 seconds if it should preload anything else (you can change that in the preload.conf file). ureadahead is the one that only runs during the boot process.

[QUOTE=Bobhuber]Decrease your swappiness to 10. I don't think you will see any difference in memory usage but you should see a vast improvement in performance. Make sure you read the whole page (it's on the bottom).[/QUOTE]

If you don't use the swap partition does decreasing swappiness really make a difference? I only have 4GB's of RAM but I never use the swap partition. Free always looks like this for me:

```


             total       used       free     shared    buffers     cached
Mem:       4009916    1539100    2470816          0      72928     493388
-/+ buffers/cache:     972784    3037132
Swap:      4455420          0    4455420

```

---

### Post by xyzzyman on 2012-01-21
Come to think of it, OP should run 

```
free
```

at a command prompt. It'll show how much RAM is also being used for cache. Also OP, what programs are taking time to load?

---

### Post by snowpine on 2012-01-21
> **xyzzyman said:**
> preload runs all the time. it reanalyzes every 20 seconds if it should preload anything else (you can change that in the preload.conf file). ureadahead is the one that only runs during the boot process.

My mistake, carry on. :)

---

### Post by kazztan0325 on 2012-01-22
By the way, what about enabling **zRam**?
However I'm not sure it would have an effect for 8GB RAM machine...

zRam stuff PPA:
[https://launchpad.net/~shnatsel/+archive/zram]("https://launchpad.net/~shnatsel/+archive/zram")

---

### Post by dcstar on 2012-01-22
> **ilovelyy said:**
> I don't use virtual machine. I just want system to cache more data so I can launch application faster. I want minimize disk write.

Make up your mind, caching more data reduces **later** disk reads by slowing down the system at a different time and forcing it to do those reads **earlier** and has nothing to do with disk writes.

---

