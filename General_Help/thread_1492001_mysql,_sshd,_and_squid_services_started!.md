---
title: "mysql, sshd, and squid services started?!"
date: 2010-05-24
forum: General Help
---

### Post by igeorgiev on 2010-05-24
Hello,

I have a very strange problem concerning the three services mysql, sshd, and squid. When I perform nmap localhost, I can see them running and listening, although I have carefully made arrangements to stop them:

1) I have opened bum and made sure they are not started automatically upon system boot.

2) I have opened rcconf tool and again made sure they are not started at boot.

3) I have checked all /etc/rcX.d and /etc/rc.local. There is no SXX link to start either of these three services. 

Basically, I have tried every possible tool and known config to make sure they are NOT started at boot time in ANY of the user levels, but still they run each time I start the machine. When I perform service mysql|sshd|squid stop, they are promptly stopped but are started again on e.g. system restart.

Any ideas are greatly appreciated! Personally, I am not super-familiar with Upstart, maybe it starts them but still no knowledge of that.

Thanks in advance for any comments.

---

### Post by cdenley on 2010-05-24
Sysv init is being replaced by upstart. Upstart doesn't use symlinks to /etc/init.d scripts in /etc/rc?.d.
```

sudo mv /etc/init/mysql.conf /etc/init.d/mysql.disabled
sudo mv /etc/init/squid3.conf /etc/init.d/squid3.disabled
sudo mv /etc/init/squid.conf /etc/init.d/squid.disabled
sudo mv /etc/init/ssh.conf /etc/init.d/ssh.disabled

```

---

### Post by igeorgiev on 2010-05-24
Thanks, it worked. Is there any GUI tool that can configure various Upstart processes at startup?

---

### Post by cdenley on 2010-05-24
> **igeorgiev said:**
> Thanks, it worked. Is there any GUI tool that can configure various Upstart processes at startup?

That that I know of, but you can configure the processes by editing the configuration files themselves.

---

