---
title: "Strange network pattern"
date: 2010-03-02
forum: General Help
---

### Post by J V on 2010-03-02
My modem/router is going to hell...

In the meantime my system monitor is showing a very strange pattern of internet traffic while trying to stream some video, and the video stops being buffered properly evey ...? seconds...

---

### Post by doas777 on 2010-03-02
hmmm. doesn't seem all that unusual to my eyes, but I may be missing whatever you are talking about.

---

### Post by J V on 2010-03-02
Internet is incredibly slow! even google.com takes...

15 seconds +- "waiting for google.com..." and then the net panel won't work cause one of the pages won't load at all...

---

### Post by doas777 on 2010-03-02
I usually find that if my internet is slow, and the problem is on my network, then it is roomates torrenting and sucking up the upstream and swamping the router with 100+ tiny connections.

---

### Post by J V on 2010-03-02
well I don't have time to go down the street and knock on every door till I get an answer...

Any built-in linux magic that can give me priority on the network? (That'll show them)

---

### Post by doas777 on 2010-03-02
> **J V said:**
> well I don't have time to go down the street and knock on every door till I get an answer...

Any built-in linux magic that can give me priority on the network? (That'll show them)
not that I know of. I take it the router is not in your possession, or that yours in not secured? I'd say one of those two is the source of your issue.

---

### Post by J V on 2010-03-02
well this router is in possession and has disabled wireless, but the entire street ends up on the same line somewhere along the way...

---

### Post by doas777 on 2010-03-02
> **J V said:**
> well this router is in possession and has disabled wireless, but the entire street ends up on the same line somewhere along the way...

in that case you will have to contact your isp. broadband uses a L2 multiplexing technique called DOCSIS (v2 or 3)  for shared access, which is all controlled by your cable modem (or whatever kind of demarc device you have), so no there is little to nothing to do in ubuntu to deal with it.

---

### Post by J V on 2010-03-02
I was thinking of hacking my ISPs mainframe actually :)

nvm, will wait till tomorrow then...

---

