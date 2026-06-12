---
title: "SSH Write failed: Broken pipe"
date: 2010-10-13
forum: General Help
---

### Post by Jimbopix on 2010-10-13
Hey everybody,

just installed 10.10 yesterday, and since installing, I get a "Write failed: Broken pipe" message and get disconnected from SSH when after it sits idle for a while. Which didn't happen on 10.04.

What I've got is a server running 10.04 on my local network that is connected to an IRC channel. I ssh into that server from my desktop and monitor the channel.

I've tried a few things so far, I've tried adding "ClientAliveInterval 30" into my ssh_config file and that seemed to do nothing. Then I tried using "ssh -o TCPKeepAlive=yes" that didn't work either. I've searched around and haven't really found anything that's working for me so far.

Anything else that could have changed between 10.04 and 10.10 that would cause this?

---

### Post by Jimbopix on 2010-10-18
switched routers and the problem went away. 

Router totally crashed on me last night. Swapped routers and everything is back to normal. The issue must have been the router failing.

---

