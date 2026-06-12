---
title: "Replacing gdm with nodm?"
date: 2011-06-12
forum: General Help
---

### Post by ojdon on 2011-06-12
Hi there, I'm running Ubuntu 11.04 with Gnome3 + Gnome-Shell installed. I want to replace gdm with nodm, how do I go about doing this?

Last time I took these steps:
> 
sudo apt-get install nodm
sudo gedit /etc/default/nodm

Then I edited this line:
> NODM_ENABLED=false
So it said true instead of false then I replaced this line:
> NODM_USER=root
With my username and saved and closed it. Then I went to edit /etc/X11/default-display-manager so it read
> /usr/sbin/nodm

But then once I restarted I just get stuck in an infinite cycle of the boot screen. So I gave it a fresh reinstall to start again. This happens with Unity and Gnome-shell so the session I'm using isn't a problem. Any ideas?

---

