---
title: "keys expired, packages not authenticated??"
date: 2010-10-21
forum: General Help
---

### Post by andres.ordonez on 2010-10-21
Hi, I get this when checking for updates from the update manager:

"
W: GPG error: [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release: The following signatures were invalid: KEYEXPIRED 1287271627 KEYEXPIRED 1287271627 KEYEXPIRED 1287271627 KEYEXPIRED 1287271627 KEYEXPIRED 1287271627 KEYEXPIRED 1287271627 KEYEXPIRED 1287271627
"

and then, when I try to install the packages (from the update manager) I get this: 

"
You are about to install software that can't be authenticated! Doing this could allow a malicious individual to damage or take control of your system.
NOT AUTHENTICATED
wgdd-archive-keyring
"

are these two "problems" related? What should I do?

Thanks

---

### Post by howefield on 2010-10-21
Go to the link in your post, you'll find information about the expiration of the keys and what to do next.

You could temporarily disable that repository by going to System > Administration > Software Sources > Other Software and deselect it. Reload your sources and try updating again.

By the way, are you running Jaunty Jackelope ?

If you are, just to mention that it goes end of life in two days time, so will be unsupported after that.

---

### Post by andres.ordonez on 2010-10-22
Thanks howefield, I disabled the jaunty repositories and that fixed it. 
(Running 10.04)

---

