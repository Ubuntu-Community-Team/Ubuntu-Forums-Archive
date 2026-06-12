---
title: "bash script : ssh + rdesktop"
date: 2010-04-24
forum: General Help
---

### Post by mrphd on 2010-04-24
can someone help me with a simple bash script? i am new to this. i want to start an ssh session (i have generated a key so this does not prompt me for a password).

#/bin/bash
ssh [email]me@a.c.org.uk[/email] -L 3392:b.c.org.uk:3389
rdesktop -u me localhost:3392 -f

when i execute the script it logs into ssh successfully, but only executes rdesktop when i exit the ssh session (which i clearly do not want). after logging in, i want rdekstop to be run in another terminal,

any help appreciated.

---

### Post by mckinnon81 on 2010-04-24
Try this:


```
#!/bin/bash
ssh [email]me@a.c.org.uk[/email] -L 3392:b.c.org.uk:3389 &
rdesktop -u me localhost:3392 -f

```

---

### Post by HermanAB on 2010-04-24
Uhmmm, this is to connect to Windows RDP?

If so, then you don't need SSH.  RDP is pretty secure.  It uses RC4.  If you are worried about something that can crack RC4, then you have bigger problems.

---

### Post by mrphd on 2010-04-24
no, I'm connecting to a Linux HPC and need to use SSH. Adding "&" does not work (it does not appear to start ssh session). Any ideas?

---

### Post by mckinnon81 on 2010-04-24
Take a look at this guide.

[http://www.g-loaded.eu/2006/11/24/auto-closing-ssh-tunnels/](http://www.g-loaded.eu/2006/11/24/auto-closing-ssh-tunnels/)

This should help you achieve what you are looking for.

---

### Post by mrphd on 2010-04-24
Thanks. Something like:

```
#/bin/bash
ssh -f me@a.c.org.uk -L 3392:b.c.org.uk:3389 sleep 10; rdesktop -u me localhost:3392 -f
```

works perfectly. Thread solved.

---

