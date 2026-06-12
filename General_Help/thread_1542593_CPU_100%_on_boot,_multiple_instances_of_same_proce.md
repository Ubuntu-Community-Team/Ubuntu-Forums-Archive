---
title: "CPU 100% on boot, multiple instances of same process"
date: 2010-07-30
forum: General Help
---

### Post by dubnmike on 2010-07-30
Hello-

I tried the google and browsing the known bugs in the sticky before posting this thread.

On boot the machine is pegged at 100%.  It is a dual-core with 4GB of ram and is running 10.04, 64bit.  Also, as time goes on it eats up all the ram till theres maybe 32mb free. What happens is there are multiple 4-10+ identical processes running.  They seem to be gnome related.

Screenshots:

[http://modestolan.com/~twentydead/heavycpu.png](http://modestolan.com/~twentydead/heavycpu.png)

The machine sits idle on my floor and runs samba and apache/mysql/gallery for my test website that no on but myself visits.

-Mike

---

### Post by linux18 on 2010-07-30
```

killall bonobo-activation-server

```

---

### Post by Yarui on 2010-07-30
What happens when you kill all those processes?  Do they just restart? I know you are probably hoping to find a way to stop this problem from occurring at all, but are you at least able to put a stop to it once it has started?

---

### Post by dubnmike on 2010-07-30
It looks like if I kill one of these:

dbus-daemon, indicator-sound-service and indicator-applet.

it restores some order.  However, there are still 1389 processes running.  As time goes on (about 2 minutes) the process count is down to 958 and continues to decrease.  However, some 800 processes are sleeping. The highest amount of processes I had before killing off dbus-daemon and indiacotr-sound-service was around 1800.

Killing bonobo kills it, but it returns with a vengence and continues to multiple.  My cpu is at about 1% though.

Several minutes later I am down to 520 processes with most of them sleeping.


**Edit

Even more time has gone by.  I am back up to 1500 processes and climbing.

[http://modestolan.com/~twentydead/moreheavycpu.png](http://modestolan.com/~twentydead/moreheavycpu.png)

---

### Post by dubnmike on 2010-08-01
bumpity.

---

### Post by dubnmike on 2010-08-12
bump.

---

