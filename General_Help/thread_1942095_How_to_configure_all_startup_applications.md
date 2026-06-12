---
title: "How to configure all startup applications?"
date: 2012-03-16
forum: General Help
---

### Post by gldearman on 2012-03-16
Hi, everyone,

Is there an easy way to list and configure *all* of the applications that run at startup?  I know that there are some that aren't being called by Gnome, because they're running at startup even in non-Gnome sessions, and because they aren't listed under System > Preferences > Startup Applications.

Specifically, I was having trouble with Gwibber upon login.  Since I don't use Gwibber, I wanted to remove it from my startup applications, but it wasn't listed in the menu.  And it even ran when I logged into a non-Gnome session.  I solved that specific problem by finding gwibber.desktop in /etc/xdg/autostart, and removing it.

But there must be an easier way to identify all of the startup applications that are launched when a user logs in.  I'm sure there are other services and applications autostarting that I don't need, and any one of them could also cause a problem. Does anyone know how to do this easily?

---

