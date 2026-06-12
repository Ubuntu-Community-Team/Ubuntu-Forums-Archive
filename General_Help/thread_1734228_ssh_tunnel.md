---
title: "ssh tunnel"
date: 2011-04-20
forum: General Help
---

### Post by duckyq on 2011-04-20
Hi all, i've created a ssh tunnel from my local ubuntu to a remote windows server 2008(freesshd), when i run a script to remotely access and update mysql database the tunnel will close itself, any suggestions on how to make the tunnel persistant?
 
Thanks

---

### Post by Lars Noodén on 2011-04-20
On the client side you can try the **ServerAliveInterval** and **ServerAliveCountMax** configuration directives.  Or on the server, if you have OpenSSH, you could set **ClientAliveInterval** and **ClientAliveCountMax**.

---

### Post by duckyq on 2011-04-20
Hi lars, i can't seem to find **ClientAliveInterval** or**ClientAliveCountMax **on my /etc/ssh/sshd_config file. where is it located?

---

### Post by Doug S on 2011-04-21
The default sshd_config file does not contain all of the possible keywords and arguments available for sshd.
If they are not in the sshd_config file, then the default values will be used. To override the defaults, add lines to the sshd_config file to set the desired values.
Use the man pages ( "man sshd_config" ) for a complete listing and the meanings.
After editing the sshd_config file (requires "sudo"), sshd needs to be restarted. ( "sudo /etc/init.d/ssh restart" ) It is recommended to keep a copy of the original sshd_config file.
I hope this helps.

---

### Post by yetiman64 on 2011-04-21
> **Doug S said:**
> ...( "sudo /etc/init/d/ssh restart" )...

@ Doug S, I think that is a typo, should be "sudo /etc/**init.d**/ssh restart"

---

