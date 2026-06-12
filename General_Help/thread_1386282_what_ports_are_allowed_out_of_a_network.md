---
title: "what ports are allowed out of a network"
date: 2010-01-20
forum: General Help
---

### Post by Jenkins1 on 2010-01-20
Hi,

I converted my family to ubuntu over the easter holidays and set up ssh so that I could access the computer at home if necessary. I have use the canyouseeme.org site to check the port is available at the home end. But at my end I am behind a university network and I can not get a connection to my home computer. How do I determine what port I can use on the university network?

Thanks in advance.

---

### Post by Roasted on 2010-01-20
While I do not have a direct answer for you, perhaps finding a port scanner would be up your alley, and just tie into that port to SSH accordingly?

Just thinking out loud...

---

### Post by wyliecoyoteuk on 2010-01-20
SSH is commonly blocked, as are many other privileged ports below 1024.

I would use a higher port (above 1024) and forward it to the SSH port on the PC in the router.

i.e. external port on your router 6331 forward to 22 on pc.

Then access it via ssh <externalipaddressofrouter>:6331

---

### Post by Jenkins1 on 2010-01-20
For the sake of explanation we will say I use port 6331.

My router at home forwards port 6331 to port 6331 as I have ssh set up on port 6331. I appear to be able to ssh out of university when working on projects on launchpad. But I don't want to use port 22 on my home router. I am already using a port above 1024 to ssh out on so some ports above 1024 must be blocked.

---

