---
title: "FreeNX problem"
date: 2006-06-11
forum: General Help
---

### Post by Coogan on 2006-06-11
I had FreeNX running great in Breezy, but had my system get hosed and upgraded to Dapper.  Now I'm trying to get FreeNX running again, and I cannot for the life of me figure out what's going wrong.  I got it installed thru the repositories and thought I had it set up correctly, but every time I try to remote in, I get this:

NX> 203 NXSSH running with pid: 3480
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 192.168.1.110 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

I've tried setting the AllowUser nx in the sshd config, imported the client keys, verified that it's pointed to the .ssh dir in the nxserver home dir, but it still will not authenticate.

Coog

---

### Post by Coogan on 2006-06-11
never mind.  I finally got it working.  Apparently the NX client on my Windows box was storing previous settings even after I uninstalled the client.  Deleting them and cleanly reinstalling fixed it.

Coog

---

