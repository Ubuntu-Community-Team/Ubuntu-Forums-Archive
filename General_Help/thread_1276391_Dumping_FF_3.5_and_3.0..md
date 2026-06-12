---
title: "Dumping FF 3.5 and 3.0."
date: 2009-09-27
forum: General Help
---

### Post by running_rabbit07 on 2009-09-27
I am possibly going to dump Firefox. After messing with Epiphany, I think Epiphany looks better and is a bit faster. 

When I uninstall Firefox via Synaptic, is it going to cause any problems?

Thanks for the answers.

---

### Post by claracc on 2009-09-27
I think the same, epiphany displays with better quality web pages, and i have decide to use epiphany 2.26.1 as predetermined browser and firefox only in cases when epiphany fails.
I would take care to uninstall firefox because epiphany uses plugins saved in firefox folders. Perhaps someone with more knowledge could advise better.
One question, could you see bbc videos with epiphany?, I can't, but i can with  firefox 3.0.14. Any other videos as youtube or embeded in newspapers can be seen with epiphanyvery well.
Regards

---

### Post by FunkyRes on 2009-09-27
In theory, removing firefox completely should not cause any problems. Any apps that need pieces of it (IE some apps historically used nspr but most of them don't anymore) should cause the needed subpackage to be retained.

As far as epiphany (and other webkit browsers) and videos - I've found that flash works but that html5 video does not work, and does not even allow flash as an alternative fallback. Because of that I changed my website design (which was using html5 video with flash fallback).

I have no idea how well the totem and other plugins work.

I really like Epiphany and Midori. I still use firefox because of the addons (notably noscript) but I especially like Midori, and as soon as webkit matures, may use it as my full time browser.

Earlier when trying to report a bug through the launchpad system, I found that neither midori or epiphany could do it, I had to use FireFox, so you may want to keep FireFox around.

---

### Post by CatKiller on 2009-09-27
> **running_rabbit07 said:**
>  When I uninstall Firefox via Synaptic, is it going to cause any problems?

The only obvious one is that removing firefox will remove the ubuntu-desktop metapackage (the list of everything that's installed by default). When you're ready to upgrade to a future Ubuntu release you may want to re-install the ubuntu-desktop metapackage.

---

### Post by lovinglinux on 2009-09-27
> **CatKiller said:**
> The only obvious one is that removing firefox will remove the ubuntu-desktop metapackage (the list of everything that's installed by default). When you're ready to upgrade to a future Ubuntu release you may want to re-install the ubuntu-desktop metapackage.

It also removes some plugins. For instance, if you remove Firefox it also removes gecko-mediaplayer.

---

### Post by Marflus on 2009-09-27
I tried epiphany and liked it for the most part, but while it's missing firebug and there's that annoying bug which means I have to set where I want to download files to every time I start the program I can't use it. Ok, so it's mainly the bug that bothers me, since I can always have firefox installed for firebug work.

That aside, I wouldn't advise removing firefox, though it shouldn't actually break anything. Some applications make use of it, so I'd err on the side of caution and keep it, even if you do want to remove it's menu entry :P

---

### Post by running_rabbit07 on 2009-09-27
Looks like I'll be keeping Firefox around then, but I'll just set the menu not to show it.

Thanks for all of the input.

---

