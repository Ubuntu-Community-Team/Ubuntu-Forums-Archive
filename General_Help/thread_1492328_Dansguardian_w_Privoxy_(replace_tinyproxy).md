---
title: "Dansguardian w/ Privoxy (replace tinyproxy)"
date: 2010-05-24
forum: General Help
---

### Post by dardack on 2010-05-24
Ok So I'm one of those having issues with Tinyproxy and newer versions of dansguardian (after 2.9.7 or w/e it is).  There is a bug for this, but has never been addressed.

That being said, I changed my proxy to privoxy.  Here is how to set them up:

[http://blog.bodhizazen.net/linux/how-to-transparent-proxy/]("http://blog.bodhizazen.net/linux/how-to-transparent-proxy/")


Not mine, but followed directions here and successfully have dansguardian filtering all users.

---

### Post by v4169sgr on 2010-06-05
I really like the look of this, BUT I'm not sure if I have configured dansguardian correctly. And if I have not configured dansguardian correctly, I'm worried that I will blow up access for all my users ...

So: -

1. How do I configure dansguardian to play nice with Privoxy? At the moment, I have ```
proxyport = 3128
``` but to be honest am not sure what this actually does ...

2. If I screw up with these iptables settings, how do I remove them [nicely] afterwards?? What is the roll-back?

Thanks in advance! :-)

---

### Post by v4169sgr on 2010-06-06
Any thoughts on this will be appreciated :-)

---

