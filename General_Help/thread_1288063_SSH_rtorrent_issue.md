---
title: "SSH rtorrent issue"
date: 2009-10-10
forum: General Help
---

### Post by NFblaze on 2009-10-10
So, I found this application for my knockoff iphone that allows me to SSH to my computer. After setting it up it seems like everytime I try to run rtorrent thru the SSH screen it gives me this:

```
error opening terminal: vt320
```

Anyone, know a way around this? Thx

---

### Post by Bachstelze on 2009-10-10
You can try changing the value of the TERM environment variable. Try

```
TERM=vt220 rtorrent
```

or other values like "xterm", "linux" or "cons25".

---

### Post by NFblaze on 2009-10-10
No luck with that method. It freezes up and then the session closes. I'll play around with it some more and see what I can get.

---

