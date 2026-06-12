---
title: "email &quot;proxy&quot; - conception question"
date: 2011-09-16
forum: General Help
---

### Post by huehnerhose on 2011-09-16
Hi!

I'm sorry if this is a realy stupid question, but I'm very frustrated. I work as a little admin for one department at an university and our email-server, adminstrated by university, not the department, often crashes, looses connection to mailboxes, denies connections and so on. 
The university seems to be not capable to fix this.

Now I thought: Isn't it possible to build up my own "mail proxy". This mail server has to fetch new mails from the "real" server, stores them. If the "real" server is down again - just talk to the proxy - he will deliver the changes when the "real" server responses again. 

Most of the time only the imap-server goes down, so sending shouldn't be the main problem. 

The only solution I see so far, is setting up an own server and using something like fetchmail to "copy" the accounts. My dream would be a very transparent solution. Something like squid for IMAP :) Are there solutions for this problem? Maybe solutions that don't need a whole mailserver (I'm not sure if I can build a more resistent mail server - only difference is, that my department is much smaller than the university :) )

Thanks!

---

