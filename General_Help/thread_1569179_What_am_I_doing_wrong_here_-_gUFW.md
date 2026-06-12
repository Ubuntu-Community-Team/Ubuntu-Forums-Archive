---
title: "What am I doing wrong here - gUFW?"
date: 2010-09-06
forum: General Help
---

### Post by zozza on 2010-09-06
Hello,

I don't understand this:

I am using gUFW.  I have "outgoing" set to "deny".  This prevents all traffic from exiting my computer.  I then created rules that ports 80 and 8080 are ALLOW OUT.  However, this does not permit me to access webpages and I have to set gUFW to "outgoing" "allow" which rather defeats the purpose of setting specific ports that are allowed to connect out.  

What am I doing wrong here?  I would have thought the settings above denied all traffic except those permitted by the specifically allowed rules (ports 80 / 8080) so why can't I access the web?

Thanks!

---

### Post by sikander3786 on 2010-09-06
Don't set "outgoing" to "deny". That will not allow the proxy server to connect to the internet and will result in a failure to retrieve the web pages from the internet to serve to the client.

Instead set "incoming" to "deny" and "outgoing" to "allow" and then add rules accordingly, which ever ports and ip address you want to allow to connect.


Edit: Take a look [here]("https://help.ubuntu.com/community/Gufw").

When "outgoing" is set to "deny", try browsing on the server and see if it can load web pages.

---

