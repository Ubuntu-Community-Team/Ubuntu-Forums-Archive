---
title: "X bridge (&quot;screen&quot; for X servers)"
date: 2009-10-05
forum: General Help
---

### Post by Zhwazi on 2009-10-05
I'm looking for an application that has a function similar to what screen does for terminals, but does it for X. I'm not looking for VNC and a whole-desktop approach to remote desktop, but something more akin to X forwarding through SSH, combined with the ability to disconnect from the session without killing the application, then reconnect to it later.

Sort of an X bridge to stand between the real X client and the real X server, which looks like a server to the client and a client to the server, but which can tolerate disconnections on the fake-client to real-server end, and support reconnecting, similar to how screen allows you to resume a session.

Does such a program exist, and if so, what's it called? Google was most unhelpful and if there's a technical name for this I'd like to know what it is, "screen for X" or anything similar brings up stuff about screen resolutions and the like.

---

