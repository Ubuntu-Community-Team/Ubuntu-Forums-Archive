---
title: "Post-login automation - SSH"
date: 2011-05-07
forum: General Help
---

### Post by nrabett on 2011-05-07
Every time I SSH into my server, I need to write a few commands before I continue using the SSH connection. The commands are to be executed on the remote machine. Whereas it is easy to execute the commands and log out directoy - this is done with e.g.

ssh nrabett ls 

- I have found no way to to this automatically after logon and stay connected. In the above example, nrabett is the "Host" specified in my ~/.ssh/config file, and in this file, it is also possible to specify port forwards etc. Ideally, I would like to be able to type

ssh nrabett

and see the commands executed automatically after login. However, I can find no option for this in the ssh_config manual. How can it be done?

---

### Post by nrabett on 2011-05-10
^

---

### Post by matt_symes on 2011-05-10
Hi

From 

```
man ssh
```> 
~/.ssh/rc
Commands in this file are executed by ssh when the user logs in,
just before the user's shell (or command) is started.  See the
sshd( 8 ) manual page for more information.I want to do something similar myself at the moment, but i have not had the time to try it yet. 

Create a file called rc in ~/.ssh on your server (i presume the server) and add your commands there. 

Please tell me if it works.

Kind regards

---

### Post by nrabett on 2011-05-11
Thanks, 
this helped me out, but I am still surprised that it cannot be done from the client side - and specifically defined for each server. 

The ~.ssh/rc file indeed makes it possible to customize server behaviour, but even the Android ssh client ConnectBot has the feature I am looking for.

---

