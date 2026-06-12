---
title: "SSH Connection drops."
date: 2010-01-08
forum: General Help
---

### Post by resadem on 2010-01-08
I have ubuntu 9.10 server installed, I am connecting with putty over ssh 22. but  after a while (about 20-30 mins) the connection drops. and I have to connect again.
could you help? why it can be? is there any configuration for that?

---

### Post by Grenage on 2010-01-08
[http://ocaoimh.ie/how-to-fix-ssh-timeout-problems/](http://ocaoimh.ie/how-to-fix-ssh-timeout-problems/)


Give that a look.

---

### Post by Lars Noodén on 2010-01-08
Try adding something like this when running the client:
    **-o "ServerAliveInterval 60"**

If that works, then add it to the client configuration file you have as ~/.ssh/config

---

