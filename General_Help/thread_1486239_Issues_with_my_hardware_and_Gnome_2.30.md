---
title: "Issues with my hardware and Gnome 2.30"
date: 2010-05-17
forum: General Help
---

### Post by lafayette on 2010-05-17
Hi all,

my first post here and my first day with Ubuntu.

I'm having big big troubles, not due to Ubuntu but I bet they have to do with Gnome.

After install, all went ok and I could log in Gnome desktop, did some operations (not changing anything related to configuration), then shut down.

At next restart, I could not get back inside gnome since an alert showed me that power-manager was still running and session was not terminated.
If I force it to terminate session, it simply hangs on a desktop screen without icons (only panels load, though they have default plain gray theme applied).

I can switch to other terminals, but every command involving sudo will make console hang forever, without any other possibility than restarting (but going nowhere again).

I suppose that there's something to do with my hardware, since I migrated from Arch Linux for the very same strange problems since I updated to Gnome 2.30: in that case, I could even see the output from the console, producing an infinite loop between gnome-settings-daemon, gnome panel and gnome power manager (refer to [http://bbs.archlinux.org/viewtopic.php?id=96371](http://bbs.archlinux.org/viewtopic.php?id=96371) this thread)

My hardware is basically AMD Thunderbird XP, with ASUS A7N8X-VM motherboard, and nothing more.

---

### Post by lafayette on 2010-05-18
Any idea at least on how I can debug more (for example, output for session started by gdm)?

---

### Post by lafayette on 2010-05-18
As the wisest knows, it's better to solve things by yourself :)

So, I noticed that all the troubles were due to ndiswrapper and my mrv8k51 driver (for an ASUS WL-138G wifi card). I removed it, and after some googling I found an old driver version that works flawlessly with my Gnome 2.30.

Everyone interested can find the topic here in Asus forum:
[http://vip.asus.com/forum/view.aspx?board_id=11&model=WL-138g&id=20070416104605031&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=11&model=WL-138g&id=20070416104605031&page=1&SLanguage=en-us)

---

