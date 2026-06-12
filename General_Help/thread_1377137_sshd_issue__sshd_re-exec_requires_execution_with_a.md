---
title: "sshd issue:  sshd re-exec requires execution with an absolute path"
date: 2010-01-09
forum: General Help
---

### Post by JockVSJock on 2010-01-09
I rebooted my computer and when trying to start sshd, continue to get the following: 

```

cmmiller@ladytron:/usr/sbin$ sudo ./sshd
sshd re-exec requires execution with an absolute path

```

There was a earlier thread on this here: 

[http://ubuntuforums.org/showthread.php?t=786281](http://ubuntuforums.org/showthread.php?t=786281)

I'm not understanding why to apt-get this to fix this.  Also when using sudo, checked $path and /usr/sbin is in it, so a bit confused here. 

Also, ssh falls under /etc/rc3.d and /etc/rc5.d, so very confused on why this isn't working...

thanks

---

