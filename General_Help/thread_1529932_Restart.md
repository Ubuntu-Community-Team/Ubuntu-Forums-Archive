---
title: "Restart?"
date: 2010-07-12
forum: General Help
---

### Post by redfox1160 on 2010-07-12
Are there multiple ways to restart Ubuntu server? I am running Ubuntu Server 10.04, and I know you can restart it with the following code```
sudo shutdown -r now
```

Also, I have heard about people who haven't had to restart their linux boxes for years, and I was wondering weather restarts whether this was necessary or not. When I logged onto my server the other day, there was a message that said I had to restart the server. I'm not sure exactly how it showed up, but it was something like this ```
Welcome to Ubuntu!
 * Documentation: https://help.ubuntu.com/
  
  System information as of Mon Jul 12 22:22:54 EDT 2010

  System load: 0.08              Memory usage: 39%   Processes:       77
  Usage of /: 9.6% of 11.39GB    Swap usage:   0%    Users logged in:  0

  Graph this data and manage this system at https://landscape.canonical.com/

0 packages can be updated.
0 updates are security updates.

**Restart Required**
Last login: Mon Jul 12 22:16:29 2010 from 192.168.0.0
user@DeepThought:~$
```

Was that restart really required? (I assume it was)
Was there something else I could have done?
Is there a way to restart the server without effecting the uptime command?
Thanks!

---

### Post by pytheas22 on 2010-07-12
You can also restart with:
```

sudo reboot
```

or:
```

sudo init 6
```

and probably other ways too.  But to answer your real question, usually when the login screen tells you a restart is required, it's because you've applied an update which can only take effect once the server is restarted.  Generally this means you've updated the kernel, which is one of the only packages that requires a restart to be updated fully (this isn't completely true; see below).

There's no way to reboot without setting your uptime back to zero.  Otherwise it wouldn't be a measure of uptime!

If you're really interested in never rebooting your server, you might want to look at [ksplice]("http://www.ksplice.com/"), which makes it possible to update the kernel without rebooting.  It's intended for enterprise environments, not casual server administrators, but it can still be interesting to play around with.

---

### Post by jerenept on 2010-07-12
sudo reboot now

---

### Post by redfox1160 on 2010-07-13
> **pytheas22 said:**
> You can also restart with:
```

sudo reboot
```

or:
```

sudo init 6
```

and probably other ways too.  But to answer your real question, usually when the login screen tells you a restart is required, it's because you've applied an update which can only take effect once the server is restarted.  Generally this means you've updated the kernel, which is one of the only packages that requires a restart to be updated fully (this isn't completely true; see below).

There's no way to reboot without setting your uptime back to zero.  Otherwise it wouldn't be a measure of uptime!

If you're really interested in never rebooting your server, you might want to look at [ksplice]("http://www.ksplice.com/"), which makes it possible to update the kernel without rebooting.  It's intended for enterprise environments, not casual server administrators, but it can still be interesting to play around with.

Thanks! My server is just a small server, so I probably wont use ksplice (I probably will look into it though!).

---

