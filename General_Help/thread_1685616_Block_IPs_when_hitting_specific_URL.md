---
title: "Block IPs when hitting specific URL"
date: 2011-02-11
forum: General Help
---

### Post by Planky on 2011-02-11
I've noticed in my Apache logs a lot of hits to a specific URL on my server. The thing is, the URL is invalid and returns a 404. Every hit has a different Agent ID (things like Windows NT 4 and IE 8, Mac OS and Safari, Windows 7 and Mozilla, etc) and usually a slightly different IP address. If you browse the URL with Chrome/Firefox, it gets reported as potential phishing activity - despite it only returning a 404 error. 

I blocked a range of IPs with IPTables which worked for a while, but I can see the IP address has changed again (outside of the range I set) and is generating logs again. 

Is it possible to automatically block any IP attempting to access this specific URL?

---

### Post by kidders on 2011-02-12
Hi there,

One option would be to run **tail -fn0 /path/to/access_log** as root, grep the output for the URL you're interested in, and pass the originating IP addresses as arguments to something like **iptables -I INPUT -s 12.34.56.78 -j DROP**.

Just be careful not to block *yourself* (or 127.0.0.1)!

Incidentally, blocking access to a URL won't do much for the phishing alert. Assuming you didn't bring the problem on yourself (ie by *intentionally* hosting something iffy), it's likely your box has been compromised. What are you serving?

---

