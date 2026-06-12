---
title: "Is there a way to restart apt"
date: 2010-04-07
forum: General Help
---

### Post by chrisbay90 on 2010-04-07
I have two sources.list file. A sources.list.proxy and a sources.list.noproxy, the first of wich points to apt-cacher on my home server and the other wich points directly to the regular repo's.

I have wicd run a script when i connect and disconect from my home network. One of the tasks being cp sources.list.proxy sources.list on connect and sources.list.noproxy sources.list on disconnect. However the repo's apt-get uses does not change until i restart my machine, clearly not a good solution. Is there a way of just restarting apt?

---

### Post by sisco311 on 2010-04-07
after you switch the files, you have to run:
```
sudo apt-get update
```

---

### Post by chrisbay90 on 2010-04-07
That worked great. Thank you [sisco311.]("http://ubuntuforums.org/member.php?u=244665")

---

### Post by sisco311 on 2010-04-07
> **chrisbay90 said:**
> That worked great. Thank you [sisco311.]("http://ubuntuforums.org/member.php?u=244665")

You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

