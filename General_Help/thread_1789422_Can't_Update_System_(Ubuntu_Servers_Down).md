---
title: "Can't Update System (Ubuntu Servers Down?)"
date: 2011-06-23
forum: General Help
---

### Post by rainleader on 2011-06-23
I'm running Ubuntu 10.10 server and tried running sudo apt-get update (which has worked in the past), but it hangs when trying to connect to security.ubuntu.com.

Has anyone else experienced this -- is it possible that Ubuntu's archive is down?

---

### Post by rainleader on 2011-06-23
Could be a firewall issue, I have port 80 open. Is there another port?

---

### Post by jerrrys on 2011-06-24
what error message do you get?

---

### Post by rainleader on 2011-06-24
> **jerrrys said:**
> what error message do you get?

That's the strange thing -- no error message, it just timed out. My iptables firewall is set to drop all connections by default, but I have an exception to allow source/destination queries on port 80.

If I set the default action to accept, it works fine. Is there some other port used by the repos that I should open?

---

