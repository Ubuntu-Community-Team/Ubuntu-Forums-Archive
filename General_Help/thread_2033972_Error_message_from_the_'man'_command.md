---
title: "Error message from the 'man' command"
date: 2012-07-27
forum: General Help
---

### Post by ArlieS on 2012-07-27
Ihave a preinstalled, system76 desktop running ubuntu 12.04. I've had it for a week, and I've been doing "apt-get update" and "apt-get upgrade" regularly, most recently yesterday.

Today I looked at a man page. The page (from section 2, i.e. system calls) displayed, but I also got:

$ man getrlimit
man: can't resolve /usr/share/man/man3/getrlimit.3.gz: No such file or directory

I find myself wondering precisely what is broken, and how to fix it - also what's broken in the installation/update scripts to produce this situation.  

Experimenting shows that other man pages still display normally, without this kind of error message, just as I thought I remembered.

I specifically checked setrlimit, among others. That produces the same section 2 man page, but no error message.

I suspect there's a man page index somewhere, and it's messed up.  The only one I know about is the one that supports "man -k", and it is indeed confused:

$ man -k setrlimit
setrlimit (2)        - get/set resource limits
vlimit (3)           - get/set resource limits
$ man -k getrlimit
getrlimit (2)        - get/set resource limits
getrlimit (3)        - get/set resource limits
ugetrlimit (2)       - get/set resource limits

I'm surprised to find that index involved with simply displaying man pages; I suspect this is a new dependency. (New == within the past 2-4 years; I'm not a big upgrader of already-working systems.) 

How do I fix this, and why isn't it happening automatically when new man pages are installed, or as part of some kind of daily (cron?) job, when Ubuntu is obviously trying to give a smooth out-of-the-box experience.

And yes, if this were Debian, I'd expect this kind of thing. I'm afraid Ubuntu's look and feel causes me to raise my standards.

---

### Post by f1tz on 2012-07-27
getrlimit.3.gz is provided by the "explain" package. I would try reinstalling that and see if it works. 

Your man pages are usually updated when you use apt-get to install or update something. This may have gotten messed up. You can also run "mandb" to update the man database.

---

