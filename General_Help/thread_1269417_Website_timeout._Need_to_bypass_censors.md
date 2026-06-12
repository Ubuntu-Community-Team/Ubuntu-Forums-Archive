---
title: "Website timeout. Need to bypass censors"
date: 2009-09-18
forum: General Help
---

### Post by opholdings on 2009-09-18
OK.

Live in Thailand and they have a new internet filtering toy.  Unfortunately it does not work well. When visiting any website it first redirects to their server and often the browser freezes.

I have found this solution for MS.  How do I do something similar in Ubuntu?

----------

Add the following line to the bottom of the file "hosts"

C:\Windows\System32\drivers\etc\hosts

It might be hidden on your system, but it will be there...

here's the line

127.0.0.1 w3.mict.go.th

What this will do is redirect any access of w3.mict.go.th to your own computer, which, unless you a running a local website, will quickly return nothing, rather than wait for w3.mict.go.th which times out after a long delay.

--------

Any ideas?

---

### Post by rocket16 on 2009-09-18
What's your Ubuntu version?

---

### Post by imbjr on 2009-09-18
> **opholdings said:**
> OK.

Live in Thailand and they have a new internet filtering toy.  Unfortunately it does not work well. When visiting any website it first redirects to their server and often the browser freezes.

I have found this solution for MS.  How do I do something similar in Ubuntu?

----------

Add the following line to the bottom of the file "hosts"

C:\Windows\System32\drivers\etc\hosts

It might be hidden on your system, but it will be there...

here's the line

127.0.0.1 w3.mict.go.th

What this will do is redirect any access of w3.mict.go.th to your own computer, which, unless you a running a local website, will quickly return nothing, rather than wait for w3.mict.go.th which times out after a long delay.

--------

Any ideas?

You will find the same hosts file @ /etc/hosts

---

### Post by 3rdalbum on 2009-09-18
Internet filtering toy, eh? My country (Australia) is going to put one of those in place too. I'll keep that /etc/hosts file edit in mind just in case we use a similar system.

---

