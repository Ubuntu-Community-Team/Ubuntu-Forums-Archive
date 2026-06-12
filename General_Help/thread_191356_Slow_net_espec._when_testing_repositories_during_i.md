---
title: "Slow net espec. when testing repositories during install"
date: 2006-06-07
forum: General Help
---

### Post by cookfromfrozen on 2006-06-07
Hey :D

I'm having some issues with my net connection in 5.10.  As I type this, I'm downloading 6.06.

I'm connected to my ADSL router through ethernet and Ubuntu configures it with DHCP during install and it seems to succeed.   

It seems to test 2 of the update repositories during install.  However, each "test" takes about 20 minutes, so the install process takes about 40 mins longer than it should.  If I unplug the router, ubuntu installs in a few minutes. (It's a 1meg conn).

When I actually get into Ubuntu, web browsing works in Firefox but is slow (more like 56k :twisted: ).  Other network apps such as gaim don't seem to work.

I thought it was a DNS issue.  The Network Tools applet seems to let me resolve addresses fine, but I noticed some apps such as the built-in IRC client can't resolve any DNS names.

I've read a lot about how this is Ubuntu and Firefox trying to use IPv6, which causes the delay and slowness as it keeps trying IPv6 and keeps falling back to v4.

Does this seem like a reasonable explaination for my problems?  I've read that creating a "bad_list", commenting out IPv6 from a file and also disabling it in Firefox should solve it.  I can't try it yet though.  Any ideas?

---

