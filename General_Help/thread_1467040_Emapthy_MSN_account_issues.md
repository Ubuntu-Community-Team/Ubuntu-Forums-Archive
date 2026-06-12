---
title: "Emapthy MSN account issues"
date: 2010-04-30
forum: General Help
---

### Post by ukblacknight on 2010-04-30
I can't connect to MSN on empathy.  For the past 5 days, it's shown the same contacts online, with no changes, so clearly something has been wrong.

I signed into Pidgin and it was fine, totally different set of contacts online than what empathy had been showing.

Now, empathy is not letting me sign into MSN (Network error), yet it's still showing the same old contacts in the contact list from before!

Anyone else having MSN related problems on empathy?

Ubuntu 10.04 x64
Facebook chat working OK
GTalk chat working OK

---

### Post by ckeilloh on 2010-04-30
I am having the same problem.

10.04 32-bit
Facebook chat and Gtalk working for me fine, it's just MSN and the associated contacts.

---

### Post by X=RT on 2010-04-30
Me too.

---

### Post by Smart Viking on 2010-04-30
Just use another messenger program. Empathy kinda sucks i think, i have found several bugs with it.

---

### Post by ukblacknight on 2010-05-01
For me, a work around is to do:

```
killall telepathy-butterfly
```

Then restart empathy.  Seems to do the trick, but I can't guarantee that it will fix it forever.


Yeah empathy is quite annoying, it annoys me that it doesn't open a conversation window when you receive a message from someone for the first time.  Also, you can't do file transfers on the MSN protocol, and they're only touch and go on Gtalk.

I'd normally use emesene, but I've started to do a slow migration over to GTalk, and the conversation themes in Empathy are great!

---

### Post by aviramof on 2010-05-01
As far as i see it empathy is not a good IM software not for now. 
She doesn't work well with account with no XPMM support or what ever it's called, 
And as as such you can't even send file to 
Msn users and etc let alone the other options like share my desktop. 

And she align messages from left to right even when you write from right to left and basicly she's
not so good and very empty IM software i prefer to use pidgin instead for now at least.

---

### Post by uaneme on 2010-05-04
Yes butterfly crashed for some reason.   killall telepathy-butterfly   That fixed it for now.   (or use system monitor to kill telepathy-butterfly)

---

### Post by occurrence on 2010-05-04
Just uinstall telepathy-butterfly.

---

