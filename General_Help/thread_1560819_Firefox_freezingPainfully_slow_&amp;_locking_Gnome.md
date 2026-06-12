---
title: "Firefox freezing/Painfully slow &amp; locking Gnome"
date: 2010-08-25
forum: General Help
---

### Post by kevpatts on 2010-08-25
Hey all,

I'm an experienced Ubuntu user now and I'm having the same problem on all 3 Lucid machines that I use.

Sometimes when I boot Firefox is absolutely fine....

Other times if I load up firefox it runs fine until I either:
[LIST]
[*]Right Click on anything (link on a page/bookmark on the toolbar/etc.)
[*]Click on a Firefox menu (File/Edit/View/etc.)
[/LIST]
then the browser will freeze, go grey and then perform the action (show the menu) exactly 30 seconds later. During those 30 seconds ONLY Firefox has frozen.

If I then click on one of the menu items Firefox will again freeze and go grey, but now, for exactly 30 seconds, my whole desktop is frozen. I can't:
[LIST]
[*]Click on the Gnome menus (Applcations/Places/System)
[*]Rotate my desktop cube
[*]Right click on my desktop
[*]etc. etc.
[/LIST]
This seems to happen about 50% of the time when I boot up so I reboot (sometimes a few times) to get it working properly. It doesn't affect any other applications as far as I can tell.

Some non-standard things installed on my machine:
[LIST]
[*]grub 0.97 (none of my machines support grub2)
[*]JBOSS server
[*]PPTP VPN
[*]ubuntu-virt-server
[*]Netbeans
[*]LAMP servers
[*]Opera & Chromium
[*]Wine
[*]RabbitVCS
[*]k3b
[/LIST]
I can't find other reports of this but it's happening on all my machines so I'm sure it's not just me affected.

Kevpatts

---

### Post by sydbat on 2010-08-25
> **kevpatts said:**
> Hey all,

I'm an experienced Ubuntu user now and I'm having the same problem on all 3 Lucid machines that I use.

Sometimes when I boot Firefox is absolutely fine....

Other times if I load up firefox it runs fine until I either:
[LIST]
[*]Right Click on anything (link on a page/bookmark on the toolbar/etc.)
[*]Click on a Firefox menu (File/Edit/View/etc.)
[/LIST]
then the browser will freeze, go grey and then perform the action (show the menu) exactly 30 seconds later. During those 30 seconds ONLY Firefox has frozen.

If I then click on one of the menu items Firefox will again freeze and go grey, but now, for exactly 30 seconds, my whole desktop is frozen. I can't:
[LIST]
[*]Click on the Gnome menus (Applcations/Places/System)
[*]Rotate my desktop cube
[*]Right click on my desktop
[*]etc. etc.
[/LIST]
This seems to happen about 50% of the time when I boot up so I reboot to get it working properly. It doesn't affect any other applications as far as I can tell.

Some non-standard things installed on my machine:
[LIST]
[*]grub 0.97 (none of my machines support grub2)
[*]JBOSS server
[*]PPTP VPN
[*]ubuntu-virt-server
[*]Netbeans
[*]LAMP servers
[*]Opera & Chromium
[*]Wine
[*]RabbitVCS
[*]k3b
[/LIST]
I can't find other reports of this but it's happening on all my machines so I'm sure it's not just me affected.

KevpattsHave you tried turning off the desktop effects and testing? Might be something to do with Compiz (or whatever eye-candy app you use).

---

### Post by kevpatts on 2010-08-25
I just tried that. The only difference is that the Firefox window no longer goes grey! Still freezes the same way though.

---

### Post by sydbat on 2010-08-25
> **kevpatts said:**
> I just tried that. The only difference is that the Firefox window no longer goes grey! Still freezes the same way though.Can you give us the specs for each box? Might be some common hardware thing. Stranger things have happened.

---

### Post by lovinglinux on 2010-08-26
If you don't have any video driver issue, then I would start by optimizing your Firefox profile databases. If you have an unoptimized database, it can slow down some features like the address bar suggestions and other stuff.

To do that use [SQLite]("https://addons.mozilla.org/en-US/firefox/addon/11198/") optimizer. for other options and more info see [http://firefox-tutorials.blogspot.com/2010/05/database-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/database-optimization.html)

If that doesn't help, then start Firefox in safe mode, to see if it is an extension messing with Firefox or create a new profile. See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by kevpatts on 2011-02-03
Hey all,

Coming back to this issue. Another thing I have notices is that when the machine boots up in the "bad" state, I don't have any audio. This kinda rules out it being a video driver issue I would have thought.

Also, it effects Empathy very badly. Empathy freezes every time I get a new message, etc. These two facts would lead me to think that it's purely an audio problem, because all of these events (except clicking menus) generate sound effects.

Does this make sense?

Kevpatts.

---

