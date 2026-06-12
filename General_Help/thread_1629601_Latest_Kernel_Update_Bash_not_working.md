---
title: "Latest Kernel Update Bash not working"
date: 2010-11-23
forum: General Help
---

### Post by kreggz on 2010-11-23
Hey,

I am running Maverick via Wubi. I just completed a Kernel upgrade and when I restart into Ubuntu it just goes to a Bash prompt. I am not sure exactly what version I updated to so I haven't logged a bug report yet. Any ideas?

Cheers,

---

### Post by galvatron408 on 2010-11-24
if it just drops you to a bash prompt, you're probably in run level 1. if it is a bash prompt that asks you to log-in, then you are in run level 3. You want to be in run level 5. try typing "sudo /sbin/init 5".

here is a wiki on run levels.
[http://en.wikipedia.org/wiki/Runlevel](http://en.wikipedia.org/wiki/Runlevel)

---

