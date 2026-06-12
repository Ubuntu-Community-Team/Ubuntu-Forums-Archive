---
title: "Error running executable. Syntax error: &quot;(&quot; unexpected"
date: 2011-03-30
forum: General Help
---

### Post by ProggerPete on 2011-03-30
I've installed ubuntu-10.10-desktop-i386 onto a vmware image with the intention of running a streaming server.([http://www.freeliberator.com](http://www.freeliberator.com) is you're interested.)

When trying to start up I'm getting an error, possibly because I'm running a different shell than it expects?

Here's what I'm getting

```

root@ubuntu:/opt/caplin/apps/caplin# sh Liberator/etc/rttpd start

Starting rttpd: 
/opt/caplin/apps/caplin/Liberator/bin/rttpd: 1: Syntax error: "(" unexpected
/opt/caplin/apps/caplin/Liberator/bin/rttpd exited with code (2)

```
or
```
root@ubuntu:/opt/caplin/apps/caplin# ./Liberator/etc/rttpd start

Starting rttpd: 
/opt/caplin/apps/caplin/Liberator/bin/rttpd: 1: Syntax error: "(" unexpected
/opt/caplin/apps/caplin/Liberator/bin/rttpd exited with code (2)

```

I know this stuff runs under solaris and ubuntu 8. I'm sure it not running on my vmware is due to my linux ignorance.

Any tips on how I fix this up?

---

### Post by lloyd_b on 2011-03-30
You're probably right about it wanting a different shell.

Could you post the contents of /opt/caplin/apps/caplin/Liberator/bin/rttpd so we can see what it's doing?  It may be expecting csh or ksh, rather than bash or sh.

Lloyd B.

---

