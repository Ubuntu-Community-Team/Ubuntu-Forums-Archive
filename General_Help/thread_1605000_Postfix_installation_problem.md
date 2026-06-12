---
title: "Postfix installation problem"
date: 2010-10-24
forum: General Help
---

### Post by Monotoko on 2010-10-24
Hi guys,

Having some issues with Postfix I was hoping you could help with :)
The issue is the fact that dpkg keeps returning an error whenever I try to install postfix for some reason.

I am using Ubuntu 10.04 Server on this machine,
```
Get:1 http://apt-cacher.lon.bitfolk.com/ubuntu/gb.archive.ubuntu.com/ubuntu/ lucid/main postfix 2.7.0-1 [1321kB]
Fetched 1321kB in 0s (4949kB/s)
Preconfiguring packages ...
Selecting previously deselected package postfix.
(Reading database ... 119401 files and directories currently installed.)
Unpacking postfix (from .../postfix_2.7.0-1_i386.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up postfix (2.7.0-1) ...
update-rc.d: /etc/init.d/postfix: file does not exist
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Monotoko on 2010-10-24
No-one?

---

### Post by Monotoko on 2010-10-25
I'l try again...

---

### Post by dcstar on 2010-10-25
> **Monotoko said:**
> Hi guys,

Having some issues with Postfix I was hoping you could help with :)
The issue is the fact that dpkg keeps returning an error whenever I try to install postfix for some reason.

I am using Ubuntu 10.04 Server on this machine,
```
Get:1 http://apt-cacher.lon.bitfolk.com/ubuntu/gb.archive.ubuntu.com/ubuntu/ lucid/main postfix 2.7.0-1 [1321kB]
Fetched 1321kB in 0s (4949kB/s)
Preconfiguring packages ...
Selecting previously deselected package postfix.
(Reading database ... 119401 files and directories currently installed.)
Unpacking postfix (from .../postfix_2.7.0-1_i386.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up postfix (2.7.0-1) ...
update-rc.d: /etc/init.d/postfix: file does not exist
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Delete the package from the apt cache and try again.

BTW, what is wrong with the official repositories?

---

### Post by Monotoko on 2010-10-25
Its my VPS setup, since there are lots of people on the system if one downloads it goes into the cache where I can download it. If it's already in the cache, then it doesn't count towards my download quota when I download it.

---

### Post by dcstar on 2010-10-25
> **Monotoko said:**
> Its my VPS setup, since there are lots of people on the system if one downloads it goes into the cache where I can download it. If it's already in the cache, then it doesn't count towards my download quota when I download it.

And if a corrupted copy ends up in the cache, you all have "free" access to a file that is useless.

---

### Post by Monotoko on 2010-10-25
It wasn't corrupt, I managed to fix it by creating a blank file in the place of /etc/init.d/postfix to cheat dpkg, then running 

```
sudo apt-get remove --purge postfix
```

Then I reinstalled, and now its all good :D

---

