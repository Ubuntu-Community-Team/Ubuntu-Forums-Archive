---
title: "Issues connecting to network printer."
date: 2012-09-14
forum: General Help
---

### Post by ne0phyte on 2012-09-14
Hello!

Im trying to install a network printer that has a static IP on my home network.

I have no issues "connecting" to the printer since the ping [the ip of the printer] is working just fine.

But when installing the printer (lpd://192.168.15.21/) I get the following "error"

idle - /usr/lib/cups/backend/lpd failed

How do I solve this issue?

EDIT: Laserjet 4050

---

### Post by Bucky Ball on 2012-09-14
Welcome.

Make and model of printer? HP and Brother are well supported by you are going to need the drivers.

---

### Post by ne0phyte on 2012-09-15
> **Bucky Ball said:**
> Welcome.

Make and model of printer? HP and Brother are well supported by you are going to need the drivers.

Thanks for you interest in solving my issue.

Fortunately, I managed to solve it by myself. The problem was that I forgot about the printservers queue, and thereby tried to redirect my "printer-installation" to a queue that did not exist.

But now it is up and running!

SOLVED! :)

---

