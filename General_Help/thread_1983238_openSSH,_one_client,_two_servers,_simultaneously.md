---
title: "openSSH, one client, two servers, simultaneously"
date: 2012-05-19
forum: General Help
---

### Post by QIII on 2012-05-19
I use openSSH and NOMACHINE NX to connect to a home server from my primary machine (that server is also exposed for secure use from my laptop when on the road via port-forwarding on a non-standard port, locked down iptables, no password authentication, key authenticatiaon only, SSH2, denyhosts is active, etc, etc)

We are getting my wife a new computer shortly and I'm nabbing her old machine for my evil purposes.  I'd like to be able to ssh to that machine, too (only behind my router with no forwarding the the port I will be using for that one), so I can have a remote desktop session active to each machine at the same time, except that I'd be doing remote desktops.

The topology I'm looking for is something like this:

My machine at my comfy desk 
|                                                                           |--> SSH --> existing Linux server (port x)  (<-- from the big bad world, port forward from router)
| --> SSH --> wife's old Windows machine (port y, not forwarded from router)


Essentially, this would be just like a LAN administrator administering more than one server at time from one machine at his desk.  As an added benefit, I wouldn't need to go over to a different machine or reboot to windows on my main machine if I needed to do some Windows development.

Can anyone point me to some good documentation?  I'm getting a million google hits that are not anything like what I am looking for.  A response in detail here would probably be beyond the scope of what one could easily describe on a forum.

Would it possibly be as easy as setting up openSSH on top of cygwin, (maybe ust PuTTY) and NOMACHINE on the Windows computer, getting things set up to allow SSH on a port for that machine, then taking the public key from the existing server and using that as the public key on the new machine? Or would that be a security nightmare?

---

