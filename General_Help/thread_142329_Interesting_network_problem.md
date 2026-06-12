---
title: "Interesting network problem"
date: 2006-03-10
forum: General Help
---

### Post by fizgig on 2006-03-10
I have an ubuntu server which is at 192.168.1.234 (static).  My laptop is dynamic and is currently 192.168.1.100.  We're both behind a NAT firewall.

I can browse from both computers to the internet just fine.  They both can ping each other too.

The problem is that when I try to browse to the server ([http://192.168.1.234](http://192.168.1.234) using firefox) to see the webpage the server hosts to my network, I'm instead redirected to an odd site: [http://archiver.rootsweb.com/th/read/COPYRIGHT/1997-07/0869409480](http://archiver.rootsweb.com/th/read/COPYRIGHT/1997-07/0869409480)

I have no idea why the redirection occurs.  I do see that when I enter that IP address in firefox, in the lower-left corner it says "Looking up matt-server" which is odd since I'm trying to browse to an IP address but that does happen to be the name of the server...

Any ideas how to troubleshoot this?

---

### Post by fizgig on 2006-03-19
My bad - the main index page has an auto-redirect to "matt-server" which resolves to that other page.  I took the audo-redirect out and all is well.  :cool:

---

