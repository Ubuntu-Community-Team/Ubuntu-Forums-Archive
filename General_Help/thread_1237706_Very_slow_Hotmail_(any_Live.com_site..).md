---
title: "Very slow Hotmail (any Live.com site..)"
date: 2009-08-11
forum: General Help
---

### Post by metalmakker on 2009-08-11
My problem is I can hardly use hotmail because it is soooo slow on my Ubuntu driven laptop. Has anyone had the same problem? Also other live.com serivces are really slow.
What could be going on?
Need more information?
let me know.

---

### Post by oj0kksn5 on 2009-08-11
have you tried pinging and trace rooting live.com ?

see if its connecting at an okay speed

---

### Post by Cope57 on 2009-08-11
You could always use [Web Page Analyzer]("http://www.websiteoptimization.com/services/analyze/") - 0.98 - from Website Optimization to determine what is making a website slow.

---

### Post by kerry_s on 2009-08-11
in your firefox:
edit-> preferences-> advanced-> encryption

change certificates to "select one automatically"

---

### Post by metalmakker on 2009-08-12
> **kerry_s said:**
> in your firefox:
edit-> preferences-> advanced-> encryption

change certificates to "select one automatically"

This didn't help. I'll have to try something else.
The problem seems to be something with authorization. When I'm in, all is fast (opening mail, responding etc.), but when I move to another live.com service  or when I switch to 'my profile' or 'my contacts' it takes about ten seconds to half a minute before it responds.

---

### Post by metalmakker on 2009-08-12
> **Cope57 said:**
> You could always use [Web Page Analyzer]("http://www.websiteoptimization.com/services/analyze/") - 0.98 - from Website Optimization to determine what is making a website slow.

I tried this (great tool by the way!) but I don't really see what the problem could be. The only thing is that it advises to reduce the use of javascript, but the advice is aimed at the builder of the site as far as I can see, not the user. I don't think Microsoft will change things just because I ask them! haha

---

### Post by metalmakker on 2009-08-12
> **sephedo said:**
> have you tried pinging and trace rooting live.com ?

see if its connecting at an okay speed

64 bytes from 62.58.34.16: icmp_seq=1 ttl=59 time=32.4 ms
64 bytes from 62.58.34.16: icmp_seq=2 ttl=59 time=32.6 ms
64 bytes from 62.58.34.16: icmp_seq=3 ttl=59 time=32.9 ms
64 bytes from 62.58.34.16: icmp_seq=4 ttl=59 time=33.2 ms
64 bytes from 62.58.34.16: icmp_seq=5 ttl=59 time=33.3 ms
64 bytes from 62.58.34.16: icmp_seq=6 ttl=59 time=33.9 ms

This is not really slow is it? Thy're the results of pinging [www.live.com](www.live.com).
[www.hotmail.com](www.hotmail.com) is another matter!! check this:
metalmakker@XXODD:~$ ping [www.hotmail.com](www.hotmail.com)
PING origin.mail.live.com (64.4.20.186) 56(84) bytes of data.
^C
--- origin.mail.live.com ping statistics ---
72 packets transmitted, 0 received, 100% packet loss, time 71559m

I cancelled it after waiting one minute. Now I am not a technician, but is this right?

---

### Post by dragos2 on 2009-08-12
It has to do with your Flash, Silverlight performance, also your graphic card might not be
running the good driver or it misses it.

---

### Post by metalmakker on 2009-08-12
> **dragos2 said:**
> It has to do with your Flash, Silverlight performance, also your graphic card might not be
running the good driver or it misses it.
You could be right, because flash is giving me trouble. I can't open medialplayers in MySpace for example. Pffff, driver update in Ubuntu, I'll have to dive in to find out how that works.
thanks!

---

