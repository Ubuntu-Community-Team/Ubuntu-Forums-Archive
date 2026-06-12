---
title: "how to make upstart NOT start ssh by default?"
date: 2011-09-23
forum: General Help
---

### Post by mathog on 2011-09-23
Back before "upstart" installing chkconfig provided a reliable way to tell when services would start.  No more.  On 11.04 for instance:

```
chkconfig --list | grep ssh
ssh                       0:off  1:off  2:off  3:off  4:off  5:off  6:off

```
However, that is clearly not accurate, since it is running:

```
ps -ef | grep sshd | grep -v grep
root       618     1  0 09:41 ?        00:00:00 /usr/sbin/sshd -D

```
So, how do I tell upstart NOT to start sshd by default?  I don't want to remove it, but I only want to start it manually. 

(Edit:  this system usually doesn't even run X11, and only has fluxbox installed, so the solution has to be at the command line level, not through some GUI tool.)

Thanks,

David Mathog

---

### Post by Dangertux on 2011-09-23
```

sudo update-rc.d -f ssh remove

```should do what you're looking for. Alternatively you can edit the upstart script in /etc/init.d

---

