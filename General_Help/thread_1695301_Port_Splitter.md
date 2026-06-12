---
title: "Port Splitter"
date: 2011-02-25
forum: General Help
---

### Post by superzanti on 2011-02-25
I have an application outputting information to port 3000 (on 127.0.0.1). I want to beable to take this port and 'split' it into two. So the same thing outputs on both port 3100 and 3200.

[COLOR="white"]xxxxxx[/COLOR]-----3100
3000--|
[COLOR="white"]xxxxxx[/COLOR]-----3200

---

### Post by superzanti on 2011-02-26
Bump

---

### Post by HermanAB on 2011-02-26
Howdy,

Read up on 'tee' and 'socat'.

---

### Post by asmoore82 on 2011-02-26
> **superzanti said:**
> outputting information to port 3000
This is confusing.
Doesn't something have to be listening &#8212; what does it output to?
Do you have to initiate this connection with a web browser?
If this is the case then it is input and output &#8212; not easy to split.

Is this ntop?

---

