---
title: "setup OpenVPN server with ubuntu?"
date: 2006-03-29
forum: General Help
---

### Post by geuis on 2006-03-29
Ok, I can really use some security geek's expertise!

I have several remote offices that have to connect into our central Win 2003 server to access a couple of programs remotely. All of our remote workstations are winXP home/pro. 

The Win2003 server sits behind a netgear FVS328 router with latest firmware updates.

I'm looking to setup a VPN server using OpenVPN that will sit behind the router as well. Each of the workstations in the remote offices will connect individually to the VPN server(there's no special setup in the offices beyond a basic DSL connection).

Are there any pre-built Linux solutions, like a specific security ISO or similar that I can install and configure onto the new server?

Or, can someone point me to some guides that would walk me through setting up the correct packages in Ubuntu?

Thanks!!!!!!

-Geuis

---

### Post by cragmonkey on 2006-03-29
I'm not so sure about the exact packages that you need/want but there is an excellent hardening article for SSH located here:

[http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts](http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts)

SSH dictionary attacks are a common brute force attack. Hope this helps

---

### Post by brentoboy on 2006-04-19
is this still a concern?

I can probably help.

I have never setup an Ubuntu OpenVPN, I am about to, which is how I found this thread.  But, I have set up a handful of windows boxes to use OpenVPN to tunnel out of a heavily firewalled college campus.
--
Are you still looking to work on this, or am I two weeks too late?

---

