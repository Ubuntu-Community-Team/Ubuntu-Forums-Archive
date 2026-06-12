---
title: "clean /tmp at shutdown"
date: 2011-12-02
forum: General Help
---

### Post by owiknowi on 2011-12-02
in pardus linux 2011.2 i can automatically clean /tmp at shutdown by adding the following line:
rm -Rf /tmp/*
to this file: /etc/conf.d/local.stop

in ubuntu 10.04.3 there's not such file? how can i clean /tmp at shutdown in u10.04.3?

thanks for any help.

---

### Post by pqwoerituytrueiwoq on 2011-12-02
[http://ubuntuforums.org/showthread.php?t=1621929&highlight=shutdown&page=2#13](http://ubuntuforums.org/showthread.php?t=1621929&highlight=shutdown&page=2#13)
read that and the few following post

---

### Post by LewisTM on 2011-12-02
This may be a bit off topic, but how about storing your tmp in RAM?
If you have several GB of RAM, just add
```
tmpfs /tmp tmpfs defaults  0 0
```
to your /etc/fstab
That will store temp files in a ramdrive, which makes the system quicker and by definition is wiped at shutdown.

---

### Post by Basher101 on 2011-12-02
> **LewisTM said:**
> This may be a bit off topic, but how about storing your tmp in RAM?
If you have several GB of RAM, just add
```
tmpfs /tmp tmpfs defaults  0 0
```
to your /etc/fstab
That will store temp files in a ramdrive, which makes the system quicker and by definition is wiped at shutdown.

Bookmarked and will try with my new computer (high-end stuff) when the parts arrive and i have assembled it...

---

### Post by efflandt on 2011-12-02
/tmp is cleared when you boot anyway.

But I am running 11.10 on SSD, so I did the tmpfs thing when I finished installing from USB before I even booted the installed system.

If you forget how to do that, just refer to /etc/fstab on install CD or live iso on USB, which use tmpfs for /tmp.

---

### Post by oldtimer7777 on 2011-12-02
I use Bleachbit and I schedule it to occur each time I shutdown the computer.. 

sudo apt-get install bleachbit
sudo bleachbit

> **owiknowi said:**
> in pardus linux 2011.2 i can automatically clean /tmp at shutdown by adding the following line:
rm -Rf /tmp/*
to this file: /etc/conf.d/local.stop

in ubuntu 10.04.3 there's not such file? how can i clean /tmp at shutdown in u10.04.3?

thanks for any help.

---

### Post by owiknowi on 2011-12-03
thank you all for your replies.

@efflandt
this would be the proper way with 'temporary' files... ;) didn't know

@LewisTM
will certainly give that a try (8gb ram, no swap) btw. setting [swapiness](https://wiki.archlinux.org/index.php/Maximizing_Performance#Swappiness) the right way, speeds up pc's with less ram

@oldtimer7777
i'm using bleachbit for a couple of years now, always run it before shutdown, but /tmp isn't empty; just the logged in user files are cleaned and not /tmp/*

@pqwoerituytrueiwoq
thanks, useful information

---

