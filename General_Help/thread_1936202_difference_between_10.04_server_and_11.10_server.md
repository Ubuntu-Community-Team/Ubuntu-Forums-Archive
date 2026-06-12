---
title: "difference between 10.04 server and 11.10 server"
date: 2012-03-05
forum: General Help
---

### Post by buffchick on 2012-03-05
so, what's the difference between ubuntu 10.04 server and 11.10 server? I can't find any decent documentation on it.

---

### Post by snowpine on 2012-03-05
At the Server level, the main difference is that 10.04 uses software from April 2010 with long-term support through April 2015, while 11.10 uses software from October 2011 and will be supported through April 2013.

Further reading material:

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)
[http://www.ubuntu.com/getubuntu/releasenotes](http://www.ubuntu.com/getubuntu/releasenotes)
[http://distrowatch.com/ubuntu](http://distrowatch.com/ubuntu)

---

### Post by buffchick on 2012-03-05
thank you much!

---

### Post by buffchick on 2012-03-05
Is there any difference in the kernels?

---

### Post by buffchick on 2012-03-05
DURP. Ignore that. Reading release notes now.

---

### Post by snowpine on 2012-03-05
> **buffchick said:**
> Is there any difference in the kernels?

Yes (as you might expect since they were released 18 months apart). Did you read my links? :)

(edit) I see you are on the right track. ;)

---

### Post by buffchick on 2012-03-05
other than kernel and software... I'm really not seeing that much of a change. oh, btrfs support. maybe I should compare to precise pangolin instead...

---

### Post by snowpine on 2012-03-05
Every package in 11.10 is 18 months newer; I'll let you decide whether that qualifies as "much of a change" for your needs. 
For a server I personally would choose 10.04 due to the long-term support. Also know that the next LTS comes out next month (12.04).

---

### Post by HiImTye on 2012-03-05
> **snowpine said:**
> Also know that the next LTS comes out next month (12.04).
yeah, I'd hold off until next month if you are looking for server stability (not that 11.10 is that unstable 5 months after release)

---

### Post by buffchick on 2012-03-06
Thanks for the replies. That's kind of exactly what I was thinking. I'll just wait till April then.

---

### Post by snowpine on 2012-03-06
Installing 12.04 next month is arguably a good choice, depending on how mission-critical your need for stability is. Many long-time users recommend **do not** recommend installing a new release until it's been tested "in the wild" and the bugs are ironed out. There will be a bug-fix 12.04.1 release after about 6 months.

10.04 is super-stable by now (after almost 2 years of bug fixes) and will be supported through April 2015, and therefore my recommendation. 

You might also find this link informative: [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

---

