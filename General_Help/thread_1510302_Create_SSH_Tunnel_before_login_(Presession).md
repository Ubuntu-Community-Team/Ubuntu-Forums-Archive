---
title: "Create SSH Tunnel before login (Presession?)"
date: 2010-06-15
forum: General Help
---

### Post by GavNav on 2010-06-15
Hi guys,

I hope you can help with a little problem I'm having.

Just give you the background:

1) Let's call the two machines, Box A and Box B.
2) OpenSSH is running on both machines.
3) Key based authentication is setup between two users on these two machines, and both can login into the other with: "ssh user@host" with no problems at all.
4) I'm also port tunnelling over SSH to encrypt some traffic between the two machines: "ssh -f -N -L 1000:HOSTNAME:1000 user@HOSTNAME"

I can obviously then use "localhost:1000" to connect Box A to port 1000 on Box B securely.

However ... and this is my problem ... I want this port tunnelling connection to be automatic when I boot the machine, e.g. "Presession" and "before" a user logs in.

I tried adding to gdm/PreSession/Default:  "ssh -f -N -L 1000:HOSTNAME:1000 user@HOSTNAME"

But the problem then is because the user is not *logged in* at this stage, it can't use the user's private key to connect to the server, and hence can't automatically create the connection.

How do I get Box A to automatically create a tunnel over a port to Box B, without any intervention from me, *prior* to any users logging in?

Any help would be much appreciated!

Kind regards,
Gavin

---

### Post by delcypher on 2010-06-15
If the user isn't logged in then you're going to have to create the tunnel as root because the user's private key is only (if you've set it up correctly) is only readable by the user and root.

You would need create some sort of script that runs the following as root.

```
ssh -f -N -L 1000:localhost:1000 -i ~username/.ssh/private-key username@hostb
```


The only thing different from the command line is that I have specified the private key to use. This is often ~/.ssh/id_rsa or ~/.ssh/id_dsa

I'm afraid however I do not know how to make a script that runs at start up before the login stage but after a network connection has been established.

---

### Post by bodhi.zazen on 2010-06-15
Manually configure your network connection and call that command with post-up

Here are some examples of how to do this (pre/post up scripts):

[http://www.debian-administration.org/articles/377](http://www.debian-administration.org/articles/377)

[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

You should be able to adapt this syntax for your use.

---

