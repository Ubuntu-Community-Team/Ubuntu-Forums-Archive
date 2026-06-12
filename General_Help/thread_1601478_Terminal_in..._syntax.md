---
title: "Terminal in... syntax"
date: 2010-10-20
forum: General Help
---

### Post by zoomiest on 2010-10-20
If I am trying to terminal into an environment with a set of static IP addresses internally, what is the syntax to pick an internal, static IP address? How do I hit the correct machine?

I just use ssh xxx.xxx.xxx.xxx to intially get in.

---

### Post by matsuzine on 2010-10-20
If you're using ssh you need to login as a user as well.  What you need is:

ssh username@host

The username is the user on the remote machine.  The host can be the host name or an ip.

If you have a firewall enabled, you will need to ensure that the firewall allows ssh on both machines.

---

