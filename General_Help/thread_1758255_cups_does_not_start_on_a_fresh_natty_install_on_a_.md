---
title: "cups does not start on a fresh natty install on a Samsung N150"
date: 2011-05-14
forum: General Help
---

### Post by Bazon on 2011-05-14
[http://localhost:631](http://localhost:631) is not reachable, typing ```
sudo /etc/init.d/cups restart
``` results in > Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service cups restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop cups ; start cups. The restart(8) utility is also available.
start: Job failed to start
typing ```
sudo service cups restart
``` leads to > restart: Unknown instance: 
typing ```
sudo service cups start
``` leads to > start: Job failed to start

What can I do to make it work?

---

### Post by Bazon on 2011-05-14
oops, I realized this only happens with an old kernel version I use because of [https://bugs.launchpad.net/linux/+bug/640100](https://bugs.launchpad.net/linux/+bug/640100) .
Anyway, I would be happy to make this work with the old kernel, too, as with the old kernel I don't have any suspend issue. 

So if anyone has an idea how to make this work with the old kernel, tips are welcome. :-)

---

