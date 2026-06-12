---
title: "Spontaneous connection to EC2"
date: 2010-06-14
forum: General Help
---

### Post by Perkins on 2010-06-14
I'm not sure which category this should get put into.  It could fit under several, so I'll put it in the general area in the hopes that somebody who knows what's going on might see it and be able to enlighten me.

So, I was cruising along here a few minutes ago, when, all of a sudden, I noticed my system monitor reporting a large amount of traffic on local loopback, with occasional bits going elsewhere...  Thing is, I didn't think I was using any programs that should have been doing that.  

So, I fired up Wireshark and took a look, and saw that my machine was talking up a storm to 174.129.241.144.  Which happens to belong to Amazon EC2...  So I assumed that Ubuntu One must be run through Amazon, and had just run a sync since I had just connected to the network.  But, being a paranoid fellow, I told it to sync again to see what happened, and the result was an entirely different set of addresses...

So, my question is, "Just what is all this encrypted traffic leaving my computer, bound for parts unknown, and not obviously coming from any service I consciously remember starting or authorising?"  Perhaps I'm over reacting, but I don't usually like it overmuch when my machines take on a mind of their own...

---

