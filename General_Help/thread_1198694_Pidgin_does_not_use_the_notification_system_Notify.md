---
title: "Pidgin does not use the notification system NotifyOSD"
date: 2009-06-27
forum: General Help
---

### Post by Daniel_le_Rouge on 2009-06-27
Hello!

I really like the notification system of Jaunty and I have already changed the behaviour of the must important applications so that they use it. But I cannot configure Pidgin to do so. I have installed and activated two plugins (notify and statenotify), but it will not work out.

Can anybody help me in getting Pidgin using the notification system?

Thanks!

Daniel

---

### Post by Andifferous on 2009-06-30
Daniel

You will want to make sure pidgin-libnotify is installed, I believe it is installed by default. Then you bring up the plugins window in pidgin and scroll all the way down to Libnotify Popups, and check the box. After that you just have to configure the plugin according to your preferences and what is available. It is also quite likely that you will not want to use guifications as things get a little confused.

I like the libnotify plugin, but have been a little disappointed by the fact that it only displays popups for when a buddy signs on or off and when you receive a message. I'd like at some point to be able to configure it to popup the same way I would configure guifications. This is because I like to know when people are away or back, etc.

Hope this solves it for you.

---

