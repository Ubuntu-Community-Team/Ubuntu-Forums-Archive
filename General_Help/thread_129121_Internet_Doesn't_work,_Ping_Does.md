---
title: "Internet Doesn't work, Ping Does"
date: 2006-02-13
forum: General Help
---

### Post by anmlcrckrs on 2006-02-13
I was working on my new Kubuntu installation on this computer and suddenly after I had added bittorrent rules to Firestarter, started up Azureus and was downloading a couple things, the internet stopped working.  I couldn't figure it out so I tried to go and disable and enable my eth0 to find out that even in admin mode I can't touch the settings on it.  I know it can ping [www.google.com](www.google.com) I tried it twice.  I had also downloaded some codecs.  The weird thing is that my laptop, which has Ubuntu on it, has the exact same problem now that I turned it on.  I'm on the windows partition on my computer now and everything works.  What is going on?

---

### Post by moephan on 2006-02-13
Could it be IPv6 issues?

Try this:

1. Open firefox and type “about:config” in the address box.
2. Search for "IPv6" and then set network.dns.disableIPv6 to true.

If you're still having trouble after that, you might want to check out:
[http://ubuntuforum.org/showthread.php?t=95350](http://ubuntuforum.org/showthread.php?t=95350)

HTH

Cheers, Rick

---

