---
title: "How to force squid to start at boot-up"
date: 2011-04-06
forum: General Help
---

### Post by RyanGT on 2011-04-06
I think I have a simple problem, but I don't seem to be able to solve it.  I am using squid with dansguardian for internet filtering.  Right now, no one can go anywhere on the internet until a sudoer starts squid with:

$sudo service squid start

I want to somehow cause squid to start automatically at boot-up or login.  This is somewhat complicated by the switch over to upstart.  I have one computer running 10.04 and another running 10.10.  There is a file called squid.conf in /etc/init/, but that doesn't seem to be enough to make the service start.  Setting up a startup application also doesn't seem to work.

What do I need to do?

Thanks,

Ryan

---

