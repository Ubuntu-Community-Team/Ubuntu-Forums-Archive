---
title: "2gb Ram 390 mb free? why?"
date: 2010-02-17
forum: General Help
---

### Post by raulrustan on 2010-02-17
my Pc Pentium 4 dual core 2 gb ram 160 hd  i can attach a picture of TOP process can you say me why only 400 mb is available? THX[IMG]http://img411.imageshack.us/img411/5896/topgg.jpg[/IMG]

---

### Post by alecz20 on 2010-02-17
You only have 390 MB of unused RAM, but that doesn't mean that you have only 390 MB available.

The difference is that a lot of your ram is cached: was used, and was not cleared, but it can be over-written when required.

Linux uses as much memory  as possible for caching. To see the actual memory used look at *System Monitor -> Resources* tab.

In your screen top shows that about 1 GB is cache/buffer, and about 500 MB is empty (unused).

Hope this clarifies things

---

### Post by LoneWolfJack on 2010-02-17
just to expand, linux will always try to max out memory because unused memory is wasted. high memory usage for caching is totally fine as long as you are not swapping. as you are using 0 bytes of swap, everything is in good order.

---

### Post by raulrustan on 2010-02-17
Thank Ale and Lone....
I now understand the concept
greetings from Argentina

---

