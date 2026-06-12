---
title: "Help With Apache Mod_Status"
date: 2009-12-19
forum: General Help
---

### Post by EagleIdaho on 2009-12-19
I have enabled Apache Mod_Status. The problem I am having is with access. If I set "Allow from" to "all" I can access from the local machine. If I set "Allow from" to 127.0.0.1, I cannot access it from the local machine and get "Forbidden Access" message. I don't want to leave "Access from all" on. Any ideas of what I am doing wrong.
 
I do notice that when I reload Apache, it gives the following message "Could not reliably determine the servers fully qualified domain name, using 127.0.1.1 for ServerName." I tried seting "Allow from" to 127.0.1.1 but still get "Forbidden Access" when I try to access it thru the browser.
 
Any help would be appreciated.
 
This problem was resolved.  I was attempting to get to the stats by using //localhost/server-status.  I should have been using //127.0.0.1/server-status. Thanks.

---

