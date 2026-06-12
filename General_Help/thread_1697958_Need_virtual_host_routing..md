---
title: "Need virtual host routing."
date: 2011-03-01
forum: General Help
---

### Post by peterlauri on 2011-03-01
Hi dear forum,

Right now we are inside of our company tunneling via one machine to access other machines. To be able to access a machine from the local machine we do:

ssh -L LOCALPORT:REMOTEHOST:REMOTEPORT user@tunnelmachine

Now I can access the REMOTEHOST:REMOTEPORT on localhost:LOCALPORT. Fine, but this is a hassle for us to every time we need to access that REMOTEHOST:REMOTEPORT we need to setup the tunnel. So the next step I was thinking of was to setup these tunneling on a dedicated server that create the tunnels over ssh and maintain them it self:

PROXYHOST : PROXYPORT - > REMOTEHOST : REMOTEPORT always, and that the tunnel is always up and accessible. So the user would connect to PROXYHOST : PROXYPORT instead of to localhost:LOCALPORT. This will make it a bit easier, as the ports will stay the same all the time. But I want to take it a bit further.

I want people to access REMOTEHOST : PORT by referring to a different ip address, that is just a shadow of the real target REMOTEHOST. The current idea is that I will setup X virtual machine inside of the PROXYHOST and then for each VM then make port forwarding on the same port that is the target port in the REMOTEHOST. However, then I need to setup multiple VM, and that will take up space and also memory consumption on the PROXYHOST.

So, is there any possibility to with one ubuntu create virtual hosts that can be accessed via a specific IP and that can have unique port forwarding/tunneling active?

/Peter

---

