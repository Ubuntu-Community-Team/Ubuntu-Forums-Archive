---
title: "XDMCP - Can I log onto an existing local session?"
date: 2006-05-25
forum: General Help
---

### Post by sugna on 2006-05-25
I have installed Ubuntu on an old pc that I access from my Windows pc via XDMCP using Cygwin/X.  I have installed Azureus on the Ubuntu box and am basically using it as a download server.  It all works fine, excpet for one thing ...

I want to be able to leave Azureus (and thus the Ubuntu session that initiated it) running even when I terminate my XDMCP connection and turn off my Windows PC.  I imagine that this would be possible by making the Ubuntu machine automatically log on a user when it is booted up, and then have Cygwin/X access that local session through XDMCP (rather than start a new remote session).

I can get Ubuntu to automatically log in, but I can't seem to access the existing local session through XDMCP.  Cygwin always seems to initiate a new session that terminates with the connection.  Am I trying to do the impossible, or is there a way to do this????

I seem to remember doing it with VNC a while back, but I'd much prefer to do it with XDMCP.

---

