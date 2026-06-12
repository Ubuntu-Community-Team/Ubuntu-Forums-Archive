---
title: "opendns is blocking dns through ssh how is that possible?"
date: 2009-09-28
forum: General Help
---

### Post by JigglyWiggly_ on 2009-09-28
So ok let's say I am in a network that blocks some sites with opendns. Me being me, I just opened putty, went to the tunnels and created a tunnel to my home ubuntu VM. It all works, when I look at my wanip I see my wanip, not the network's ip I am on. So that means it works, but if I go to a blocked site a generic opendns page comes up, but not the one from the network. Like there is no branding like normally, it just says opendns. This is really weird, anyone got any ideas?

(Also I told it to connect under system > preferences > proxy, I use a socks proxy)

---

### Post by Giblet5 on 2009-09-28
How are you "going to a site"?

Are you starting firefox on the tunneled virtual (remote)?

That should work just fine.

Supply your command line (change the hostnames) for ssh, and be clear about what you execute locally and what executes on the remote.

---

### Post by JigglyWiggly_ on 2009-09-28
I did cat /etc/resolv.conf
and I got this:

nameserver 10.10.10.10
nameserver 10.10.20.11
root@3dslice:~# 

Hmm, so it's using the network's dns server.

---

### Post by JigglyWiggly_ on 2009-09-28
I even changed my dns server to a public cisco one, and it still doesn't work :?

---

### Post by Giblet5 on 2009-09-28
Again, you haven't explained what you're doing.

/etc/resolv.conf: local or remote?

Local shouldn't change. Remote shouldn't change. Not with ssh.

Are you confusing terms: OpenDNS v OpenVPN?

---

### Post by JigglyWiggly_ on 2009-09-28
Nah, I'm not confused. I switched the dns servers now, and it works after rebooting. I am probably just wording it wrong in text.

---

