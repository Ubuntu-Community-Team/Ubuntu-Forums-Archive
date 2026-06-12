---
title: "freenx stopped working when I configured no-password ssh"
date: 2010-04-23
forum: General Help
---

### Post by rbrcurtis on 2010-04-23
Hi!

So I configured my ubuntu machine and my macbook to allow me to ssh to the ubuntu machine without a password, using this tutorial: [http://breckyunits.com/code/ssh_into_your_server_without_a_password](http://breckyunits.com/code/ssh_into_your_server_without_a_password)

Ever since then, I can't connect with freeNX.  This is the error that I get:

NX> 203 NXSSH running with pid: 8461
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.100 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.



I have tried just undoing the setup instructions, but they were vague enough on modifying sshd_config that I don't think I am undoing it correctly.  Plus I like being able to ssh to my ubuntu machine without a password.  ;)

So, does anyone have any idea how to fix freeNX?  I've un/reinstalled both the server and the client and that hasn't helped.

Thanks!

---

