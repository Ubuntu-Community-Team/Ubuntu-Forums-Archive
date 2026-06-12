---
title: "Not automatically starting smbd (upstart event)"
date: 2011-01-09
forum: General Help
---

### Post by amsterdamharu on 2011-01-09
I have posted this somewhere here before and solved it but can't seem to find it. Just waisted 50 minutes googling and checking man pages for upstart.

By the way; are man pages written by someone using their tows to type and getting beaten by a stick for every character they type? It seems missing a lot of info.

Anyway, I know smbd is started with /etc/init/smbd.conf and there is a line like:
```
start on local-filesystems
```

Now it needs to be started on ????? (manually) I can't seem to find any useful information but did seem to find the upstart man pages a hundred times or so (same info same missing parts). 

I would love to get involved writing documentation for these things if only I know what I was doing.

---

### Post by sisco311 on 2011-01-10
If you are using 10.04 you can install jobs-admin. 

> jobs-admin is a simple GTK+ utility that allows any administrator to easily
 configure jobs (services) present on their system. Jobs may be enabled and
 disabled, started and stopped, and can even provide tweakable settings about
 services.


If you want to disable it manually, simply comment out the **start on** stanza:
```
#start on local-filesystems
```

BTW, you can use the Search menu at the top of the page to search for your threads/posts.

---

### Post by amsterdamharu on 2011-01-10
Thank you for your reply.

I am on Lucid but no jobs-admin available, only since maverick and up:
[http://packages.ubuntu.com/maverick/admin/jobs-admin](http://packages.ubuntu.com/maverick/admin/jobs-admin) (links on the top only available for maverick and natty)

Found it in the search, the thing is I posted the origional for portmap so must have put in the wrong keywords for my search:
[http://ubuntuforums.org/showthread.php?t=1535964&highlight=amsterdamharu+services](http://ubuntuforums.org/showthread.php?t=1535964&highlight=amsterdamharu+services)

This seems to work as well:[FONT=monospace]
[/FONT]start on [B]start-smbd
[/B]

---

### Post by febzdipo on 2011-09-27
Hi all,

I'm a newbie in upstart (not complete reading the man yet). But I have the similar problem with my ubuntu 10.10, my samba service is started on system start-up, but for the samba share to work properly I have to login and restart the service. After struggeling with googling + reading manuals (I'm a lazy manual reader), I tried to make the dependency of smbd to be the same with nmbd (/etc/init/smbd.conf vs /etc/nmbd.conf) :

start on (local-filesystems and net-device-up IFACE!=lo)

then it is working properly as it should be. Is it the proper way to do it, or I fix it the wrong way?

Thanks

---

