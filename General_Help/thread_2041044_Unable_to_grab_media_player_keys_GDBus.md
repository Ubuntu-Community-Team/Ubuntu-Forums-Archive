---
title: "Unable to grab media player keys: GDBus"
date: 2012-08-11
forum: General Help
---

### Post by Mr. Beekeeper on 2012-08-11
I was SSH-ing into my server with X forwarding and starting Rhythmbox so I can control the stereo (on my server) via my netbook.  I kept getting this error:

Unable to grab media player keys: GDBus

[B]I fixed it by changing these settings on the server:
[/B]
I went into System>Users & Groups>*MYUSERNAME*>User Privileges

and checked "use audio devices"

Now I can control Rhythmbox via X11 forwarding over ssh and can HEAR it too.  I posted this because there was nothing recent when I searched for it.  I hope this will help someone else.

---

