---
title: "memcached not loading on startup"
date: 2009-08-19
forum: General Help
---

### Post by memcachehelp on 2009-08-19
Hi Everyone,
I don't know if this is the right place to post this thread but I couldn't think of any other place. 

I need urgent help cause I'm so frustrated. I've installed ubuntu 9.04, apache2, php5 and everything works just fine. Now I'm trying to install MEMCACHED. So I installed libevent, pfp5-memcache and memcached. It works fine when I manually start it but if restart the system, it just doesn't fire on startup (I can't manually do it everytime). 

I've search all over the internet and everyone says that immediately after installation memcached is automatically enabled (even on boot) - not in my case though! 

Can someone PLEASE help, I am exausted!

Thanks in advance to all of you who have brains out there...

---

### Post by jameskw on 2009-10-06
My problem wasn't that memcached wasn't starting, but that it was starting and then dying again by the time I was logged on.

I fixed this by moving the startup script from runlevel 2 to runlevel s.

Remove 'S20memcached' from '/etc/init.d/rc2.d' and place it in '/etc/init.d/rcS.d'

No idea why that worked but it did - hope it helps someone.

---

### Post by loop23 on 2009-10-07
I tought that maybe some environment variable which is set when a normal user runs "sudo /etc/init.d/memcached start" happens not to be set when it's run during boot. 

To prove the theory, i exported some interesting vars towards the start of /etc/init.d/memcached ... and it starts fine! (this also works as an alternative workaround).
This may be the solution of a number of reported bugs for various versions... I grepped for ENV in /usr/share/memcached/scripts/start-memcached and getenv in package source, but found nothing interesting, so I assume it's some linked library that misbehaves... but unfortunatlely have no time to nail it down!

In case you like my workaround more than the previous one, vars i defined just below the comments in startup script are:

```

# Short-Description:    memcached - Memory caching daemon
# Description:          memcached - Memory caching daemon 
### END INIT INFO

export TERM=xterm
export SHELL=/bin/bash
export USER=loop
export USERNAME=loop
export LANG=en_US.UTF-8
export HOME=/home/loop
export LOGNAME=loop

```(replace my login name with yours!)

---

### Post by mattalexx on 2010-09-16
I found a simpler answer here for the same problem in Ubuntu 9.10

[https://answers.launchpad.net/ubuntu/+question/87423](https://answers.launchpad.net/ubuntu/+question/87423)

---

