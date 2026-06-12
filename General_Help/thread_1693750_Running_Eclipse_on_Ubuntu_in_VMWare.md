---
title: "Running Eclipse on Ubuntu in VMWare"
date: 2011-02-23
forum: General Help
---

### Post by sjd-mgoblue on 2011-02-23
I have Ubuntu 10.10 Maverick Meerkat.  I am running it inside a VMWare player virtual machine.  I am trying to access the Eclipse CVS repository, but when I try to expand the HEAD node, I get the following error:

[IMG]file:///C:/Users/sdoerr/AppData/Local/Temp/moz-screenshot.png[/IMG][IMG]file:///C:/Users/sdoerr/AppData/Local/Temp/moz-screenshot-1.png[/IMG]"Error fetching resource list from repository.

 Reason:
 Could not connect to :pserver:anonymous@dev.eclipse.org/cvsroot/eclipse:
 Cannot connect to host: connection refused"

When I try to telnet to proxy.eclipse.org, I get the following:

"Trying 206.191,52.48...
 Unable to connect to remote host:  Connection refused"

When I put the address above into Firefox, I get the following message:

"CVS [pserver aborted]: bad auth protocol start: GET / HTTP/1.0"

Any ideas what I could do to get through this would be helpful.  Let me know if I would be better served to visit the Eclipse forum.

Thanks.

---

