---
title: "How can I learn what port I need to open to run ddclient?"
date: 2011-07-10
forum: General Help
---

### Post by nrundy on 2011-07-10
I want to use ddclient to dynamically update my IP address. Since I use GUFW to reject outgoing unless I allow it, How can I learn what port I need to open so ddclient can work?

This is easy to do with a MS Windows firewall because I can look at the firewall log and it will tell me the app name and the port. Plus a Windows firewall will give a popup when the event occurs asking me to allow or block.

ubuntu's Log File Viewer shows several blocked connections and several blocked ports. No where is the application listed that was trying to connect out for these blocked connections.

So how can I learn the information that I need?

---

### Post by gmargo on 2011-07-10
As you can see from the Perl source code in /usr/sbin/ddclient, the IP address updates generally use HTTP.  But it depends on which service you are updating.  Is your ddclient failing to update?  What service are you using?

---

### Post by nrundy on 2011-07-10
yeah, its not updating.

using opendns.

ports 80 and 443 are open. don't know why its not updating

---

### Post by gmargo on 2011-07-10
I wasn't aware that OpenDNS provided a Dynamic DNS service. How are you configuring ddclient?

---

### Post by nrundy on 2011-07-10
just how it says here: [http://www.opendns.com/support/article/101](http://www.opendns.com/support/article/101)

---

