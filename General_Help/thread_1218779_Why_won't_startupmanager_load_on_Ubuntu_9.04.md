---
title: "Why won't startupmanager load on Ubuntu 9.04?"
date: 2009-07-21
forum: General Help
---

### Post by Codix121 on 2009-07-21
Does startupmanager come with 9.04?
it's not under my system> admin>

and when I try to run it under terminal:
```
gksudo startupmanager
```

it acts like it's loading something but nothing opens?
and I tried it a few times, once it asked me for my admin password,
but still nothing opened?

Any idea why it's not opening?
I'm not even getting an error,
it's just not opening...

---

### Post by jenkinbr on 2009-07-21
No, startupmanager is not part of the default install

[Apt-url to install startupmanager](apt:startupmanager)

Click the above link.  It is an apt-url, and should install the program for you.

If the link doesn't work for some reason, open a terminal and run the code below.

```
sudo apt-get install startupmanager
```

---

### Post by Codix121 on 2009-07-21
Thanks a million man!
Now I just look like an idiot but this did solve my question,
thank you!

---

### Post by jenkinbr on 2009-07-21
No problem

There's no such thing as a dumb question (although some tend to make you feel that way)  Trust me, we were all new once :).

---

