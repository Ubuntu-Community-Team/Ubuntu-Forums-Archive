---
title: "gm-notify no icon in system tray"
date: 2009-07-11
forum: General Help
---

### Post by varun.net on 2009-07-11
Hi,
Thanks for taking a look at this post.

I installed gm-notify.py from the multiverse repo, currently installed version is 0.8. When I run it with the following command gm-notify.py I get the initial notification but there is no icon that appears in the system tray.

What is causing this?
Can this be fixed?
What more info can I provide to diagnose this problem?

Thanks for your help.

Varun

---

### Post by marshcast on 2011-02-04
Bump

I have the same problem.

there's nothing in the settings that i remember (although I can't get to them now because there's no icon!), and nothing in gconf.xml that looks relevant.

have:

 apt-get autoremove gm-notify
 removed config .gconf/apps/gm-notify/gconf.xml
 apt-get install gm-notify

but no joy... am at a bit of a loss.

prefer this app to gmail-notify so would prefer not to switch, but...

well, I wait in hope :)

---

