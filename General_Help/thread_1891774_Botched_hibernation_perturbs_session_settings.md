---
title: "Botched hibernation perturbs session settings"
date: 2011-12-06
forum: General Help
---

### Post by anubeon on 2011-12-06
Greetings All,

A couple of days ago I attempted to hibernate my laptop. Upon rebooting the following morning it became apparent that hibernation had failed, and upon logging in it became apparent that the aforementioned botched hibernation had messed up my session settings. 

From the outset, it was apparent that my gtk+ and icon themes had not been applied, attributable to the fact that gnome-settings-daemon no longer starts automatically. A manual start (of gnome-settings-daemon) fixes this minor annoyance. It later became apparent that the majority of system settings launchers where no longer available within the system settings control panel (see attached screenshot) and that gksu could not be summoned via GUI interfaces (i.e. starting Synaptic via Synapse/GnomeDo, unlocking admin tasks within Ubuntu-Tweak and the Users & Groups dialogue, etc...) although it could still be summoned via terminal (i.e. gksu synaptic &).

I've attempted to rectify the situation by reinstalling every installed package from within synaptic package manager, but unfortunately this do not work. I'm afraid I don't know enough about Ubuntu/Linux to fix this. Any idea's how I might go about resetting/reconfiguring my session settings without having to resort to creating a brand new user account or worse, a fresh install).

Your assistance would be greatly appreciated.

P.S.: I've posted the same query at AskUbuntu, so feel free to respond either here or [there]("http://askubuntu.com/questions/85294/most-launchers-missing-from-ubuntu-system-settings-dialogue-after-botched-hibern").

P.P.S.: I'm running an up to date Ubuntu 11.10 (Oneiric Ocelot) x86-64 system.

[IMG]http://i.stack.imgur.com/IpVYE.png[/IMG]

---

### Post by anubeon on 2011-12-08
No ideas?

---

