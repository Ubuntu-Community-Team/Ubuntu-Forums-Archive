---
title: "ssh bash completion"
date: 2009-11-24
forum: General Help
---

### Post by jlward4th on 2009-11-24
I'm using karmic and it seems that recently something broke with ssh bash completion of host names.  I have my .ssh/config file configured like:
```
HashKnownHosts no
Port 2222
```

The problem is that when a new host gets added to my .ssh/known_hosts file it now uses a different format that I assume is breaking the bash completion stuff.  Here is an example:
```
host1.foo.net ssh-rsa ...
[host2.foo.net]:2222,[12.23.34.45]:2222 ssh-rsa ...
```

The first known host (which I manually edited to the old format) gets hinted fine.  The second host does not.

I can go in and manually fix my known_hosts file every time I ssh to a new host.  But I was wondering if there is an easier way to deal with this.

Thanks.

---

### Post by diesch on 2009-11-24
You could fix (or replace) _known_hosts() in /etc/bash_completion.

In any case please file a bug report for bash-completion

---

