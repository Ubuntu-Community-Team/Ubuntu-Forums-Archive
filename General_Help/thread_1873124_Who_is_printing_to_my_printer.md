---
title: "Who is printing to my printer??"
date: 2011-10-31
forum: General Help
---

### Post by conradin on 2011-10-31
I have some odd materials randomly hitting a printer. an HP laserjet 2300,
I see no internal logs in the control panel. What can I do to track down who is printing to my printer?
Is there a way to filter iptraf logging to look for destinations of a specific IP address?

---

### Post by prodigy_ on 2011-10-31
Well, if your printer is open to an untrusted network (WiFi with no security?) it could be anyone. Moreover, a lot more might be happening on such a network without you even knowing. The best solution is to turn the security on or to separate a private segment with a firewall.

If it's a corporate environment then you probably want to adjust sharing options to prevent unauthorized access.

---

### Post by conradin on 2011-11-01
corporate network, printer is straight to the wall, im not buying hardware for them. I set a filter in iptraf to monitor for in coming connections to that ip. That might be the best I can do. Though I want to keep this thread open for suggestions.

---

### Post by pqwoerituytrueiwoq on 2011-11-01
is this your own printer?

someone probably just sent it to the wrong printer or you have a duplicate ip address issue on the printer

---

### Post by iponeverything on 2011-11-01
If the printer goes strait to the wall, you'll need add a hub or transparent bridge between the wall and printer for iptraff or other tools to get a window into the IP traffic, otherwise you'll only to be seeing broadcasts.

---

