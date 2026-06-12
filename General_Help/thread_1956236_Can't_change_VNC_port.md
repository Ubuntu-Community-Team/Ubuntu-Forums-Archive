---
title: "Can't change VNC port"
date: 2012-04-10
forum: General Help
---

### Post by ayozito on 2012-04-10
Hi!

As far as I remember, for change the default port of VNC I have to go to desktop -> gnome -> remote access on the gconf-editor and there is the options for configure the server.

Now I am going there but don't have such options. I haven't the use alternative_port and the key for change the alternative port neither. I only have there: authentication_method, enabled, promt_enabled and vnc_password.

So how can I change it?

---

### Post by XCan on 2012-04-11
I am having this problem as well. Somehow someone thought it was a good idea to remove this functionality... It appears that one would have to use iptables to change the default port, which is truly a suboptimal solution. *sigh*

---

### Post by ayozito on 2012-04-13
I found it. Isn't in gconf but in dconf.

---

