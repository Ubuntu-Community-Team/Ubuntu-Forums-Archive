---
title: "Transmission web interface only available when Transmission client is running"
date: 2010-12-05
forum: General Help
---

### Post by busydoingnothing on 2010-12-05
Hey guys, I can only access the Transmission web interface while the Transmission-gtk client is running. When I close it, the web interface is no longer available. I try to manually start the transmission-daemon, but the process never shows up as running. Any thoughts?

---

### Post by DaithiF on 2010-12-05
probably a stupid question (on my part), but do you have transmission-daemon installed?  (Default install doesn't include the  daemon package, just the client)

---

### Post by busydoingnothing on 2010-12-10
> **DaithiF said:**
> probably a stupid question (on my part), but do you have transmission-daemon installed?  (Default install doesn't include the  daemon package, just the client)

Yes, it is installed. I've gotten a little further, and it seems I can only launch the transmission-daemon when I run it in the foreground:

sudo transmission-daemon -f

---

