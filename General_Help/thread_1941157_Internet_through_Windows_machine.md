---
title: "Internet through Windows machine"
date: 2012-03-15
forum: General Help
---

### Post by mohanradhakrishnan on 2012-03-15
Due to a haphazard organizational structure our infrastructure team wouldn't connect my Ubuntu 11.10 machine to the internet. But my Windows machine can connect to the internet and ubuntu can connect to windows. Ours is a NTLM proxy.
 
Can I route the internet connection of my Ubuntu - browser and command-line - via my Windows cntlm proxy. cntlm is running in windows and tested there.
 
I believe what I am solving here is a weird people issue. 
 
Thanks,
Mohan

---

### Post by dandnsmith on 2012-03-15
I don't know anything about *cntlm*, so I'd be looking at Windows Internet Sharing (which you can set up on your Windows PC, provided you are allowed, and have the ability to configure it).
That would give you the ability to share the connection, and do all the routing for you, without tying you to any particular set of protocols.
You might have to set the Ubuntu's IP address manually.

---

