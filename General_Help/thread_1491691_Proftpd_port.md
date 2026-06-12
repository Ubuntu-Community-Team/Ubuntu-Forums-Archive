---
title: "Proftpd port"
date: 2010-05-23
forum: General Help
---

### Post by NotKeith on 2010-05-23
Hi,
   I'm running Ubuntu 9.10, and am trying to get proftpd to listen on a port other than 22.  I've modified the proftpd.conf file, as well as adding the desired port to my /etc/services file, yet if I try anything other than port 22, the connection is refused.  Anything I'm missing?

Thanks!

---

### Post by cariboo on 2010-05-24
Port 22 is usually reserved for ssh, Ftp usually uses port 21.

---

### Post by Skidbladniir on 2010-05-24
```

/etc/init.d/proftpd restart

```

You have to restart the daemon for it to reload it's configuration file(s).

---

### Post by NotKeith on 2010-05-24
> **Skidbladniir said:**
> ```

/etc/init.d/proftpd restart

```You have to restart the daemon for it to reload it's configuration file(s).

I've tried that, as well as rebooting the computer, to no avail.  That command gives me the message ```
ProFTPd is started from inetd/xinetd 
```

---

