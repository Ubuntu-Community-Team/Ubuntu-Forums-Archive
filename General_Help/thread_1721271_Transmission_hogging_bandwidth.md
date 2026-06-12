---
title: "Transmission hogging bandwidth?"
date: 2011-04-04
forum: General Help
---

### Post by Hjaltlander on 2011-04-04
Hi all,

I am running a fairly standard 32bit 10.10 install, although I deleted Firefox and installed Chrome.

I am using Transmission for my torrent downloads. After a lot of reading and trying different things, I have managed to get the port to open. But I seem to have another problem and need a little help.

When Transmission is running, even if only uploading and downloading a few k each way, I have great difficulty in getting Chrome to load a web page, it is as if Transmission is hogging all the available bandwidth? Obviously if I shut down Transmission the problem goes away. It also occurred with Firefox before I deleted it.

Any ideas? Karl

---

### Post by Grenage on 2011-04-04
That's rather common, especially when the internet access point is a home (cheap) router gateway; there are too many connections for it to cope with.  Try reducing the maximum number of connections within Transmission.

This is far more common in a shared environment, where two or more people are using the connection - but it can still happen.

---

### Post by Hjaltlander on 2011-04-04
Thanks for the quick reply, but unless I am blind (which is possible) I cannot seem to find how to reduce the connections within Transmission. I can see where to reduce the number of peers per torrent or overall, but not the number of connections.

Any clue would be good, Karl

---

### Post by Grenage on 2011-04-04
Limiting the number of peers will limit the number of connections; what is it set to?

---

### Post by Hjaltlander on 2011-04-04
Ahh I see, well at the moment it is set to 60 per or 240 overall.


Karl

---

### Post by Hjaltlander on 2011-04-04
I just dropped them both by half, 30 per and 120 overall, and it does seem to be better, thanks for that. 

Karl

---

### Post by Grenage on 2011-04-04
Speed depends on both number of peers, and the speed of those peers.  A good tracker/peer base (private) can max your connection with only 1 peer; a public tracker will usually require many more.

Try setting the per-torrent limit to 20, and the global to 60.

Edit:

> **Hjaltlander said:**
> I just dropped them both by half, 30 per and 120 overall, and it does seem to be better, thanks for that. 

Karl

Glad to hear it!

---

