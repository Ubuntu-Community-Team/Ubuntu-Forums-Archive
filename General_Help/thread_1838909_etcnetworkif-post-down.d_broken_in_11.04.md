---
title: "/etc/network/if-post-down.d/ broken in 11.04?"
date: 2011-09-04
forum: General Help
---

### Post by Frozen Forest on 2011-09-04
I noticed that /etc/network/if-post-down.d and /etc/network/if-down.d/ doesn't run on natty, I put a script for saving iptables in both these location but it never execute. Strange thing is that I got a server running Ubuntu Server 10.04 and on that machine does the script execute on shutdown. I found that this problem isn't new from this link¹ but it was related to the Hardy release. The diffrence between the server and this desktop, is that the server is running 32-bit while desktop uses 64bit, could this be the cause of the problem or might there be something else. Is there a workaround?

¹ [http://ubuntuforums.org/showthread.php?t=1697380](http://ubuntuforums.org/showthread.php?t=1697380)
```

ls -l /etc/rc*.d/*networking*
lrwxrwxrwx 1 root root 20 2011-04-29 17:01 /etc/rc0.d/S35networking -> ../init.d/networking
lrwxrwxrwx 1 root root 20 2011-04-29 17:01 /etc/rc6.d/S35networking -> ../init.d/networking

```[PHP]
/etc/network$ ls -lrt if-* | grep iptablessave
-rwxr-xr-x 1 root root   77 2011-08-28 18:54 iptablessave
-rwxr-xr-x 1 root root  77 2011-09-04 20:06 iptablessave
[/PHP][PHP]
cat if-post-down.d/iptablessave 
#!/bin/sh
/bin/bash -c "/sbin/iptables-save -c > /etc/iptables.rules"
exit 0
[/PHP]

---

