---
title: "What is /var/tux"
date: 2011-09-23
forum: General Help
---

### Post by cj13579 on 2011-09-23
Hi all, this is more of a curiosity than a problem (I think) - what an earth is in /var/tux and what is it doing?

I have had a google and can't seem to find anything on it and there doesn't seem to be a man page about it. I only discovered it because I was going through my auth.log and my cron.log and I am seeing lots of cron jobs trying to run (every minute) as root. Also, it seems to create a wtmp and lastlog file in the /var/log directory but they are binary files!

Any light that can be shed appreciated!!

---

### Post by Dangertux on 2011-09-23
> **cj13579 said:**
> Hi all, this is more of a curiosity than a problem (I think) - what an earth is in /var/tux and what is it doing?

I have had a google and can't seem to find anything on it and there doesn't seem to be a man page about it. I only discovered it because I was going through my auth.log and my cron.log and I am seeing lots of cron jobs trying to run (every minute) as root. Also, it seems to create a wtmp and lastlog file in the /var/log directory but they are binary files!

Any light that can be shed appreciated!!

It's usually created by the tux webserver [http://en.wikipedia.org/wiki/TUX_web_server](http://en.wikipedia.org/wiki/TUX_web_server)

and the cron jobs are likely tuxstat (/usr/sbin/tuxstat)

That's all I've ever seen it involved with, it's usually seen more often on redhat based distros.

---

### Post by cj13579 on 2011-09-26
OK, cool. Thank you very much. I will have to have a look around and see what the hell I might have installed that would have included that!

I will mark as solved.

Chris

---

