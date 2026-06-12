---
title: "DNS Alias"
date: 2010-06-28
forum: General Help
---

### Post by cancer10 on 2010-06-28
Hi

Is there anyway we can add a local domain alias so that if we enter [http://myname/](http://myname/) in the browser it would point to [http://localhost](http://localhost)


In Windows XP I used to do it by editing the "hosts" file from the following directory

```
C:\WINDOWS\system32\drivers\etc\
```

```

127.0.0.1       localhost
127.0.0.1	myname

```

How do we do the same thing on Ubuntu 9.04?



Thanks in advance

---

### Post by dino99 on 2010-06-28
edit hosts:

sudo gedit /etc/hosts

you can put here the same info you do on windoz, like:

#<localhost>
127.0.0.1 	localhost
127.0.0.1 	localhost.localdomain
255.255.255.255	broadcasthost
::1		localhost
127.0.0.1 	local
#</localhost>

[http://ubuntuforums.org/showthread.php?t=3407](http://ubuntuforums.org/showthread.php?t=3407)

---

### Post by dcstar on 2010-06-28
> **cancer10 said:**
> Hi

Is there anyway we can add a local domain alias so that if we enter [http://myname/](http://myname/) in the browser it would point to [http://localhost](http://localhost)


In Windows XP I used to do it by editing the "hosts" file from the following directory

```
C:\WINDOWS\system32\drivers\etc\
```

```

127.0.0.1       localhost
127.0.0.1	myname

```

How do we do the same thing on Ubuntu 9.04?

Thanks in advance

In Linux there are these things called man pages, for example:

```
man hosts
```

---

