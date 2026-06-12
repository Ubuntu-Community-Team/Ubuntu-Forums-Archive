---
title: "VirtualBox ssh from guest to host"
date: 2012-01-31
forum: General Help
---

### Post by chez17 on 2012-01-31
I can't ssh from my guest server to the host in VirtualBox 4.1.2. I can successfully ssh in with no issues. There are 2 network adapters enabled, using NAT and Host-only. I have tried sshing to the various addresses that come up in ifconfig. The host is Ubuntu 11.10 and the guest is Ubuntu 11.10 server.

If I ssh to the actual ip address of my host machine it just hangs. I do have openssh-server installed so it's not that. If I try one of the local addresses I get a connection refused error.

I'm not sure what else to do and there is very little information on google that deals with going from guest to host. Any help is most appreciated.

---

### Post by Paddy Landau on 2012-02-01
I really don't know much about this, but as no one has answered you, I'll give my tiny piece of possible help.

I would use a Bridged network for your virtual machine (it's in the VM's settings within Virtual Box), so that your router sees host and guest as different computers rather than the same. Try that and let us know what happens.

---

