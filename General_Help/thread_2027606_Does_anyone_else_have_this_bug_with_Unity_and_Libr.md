---
title: "Does anyone else have this bug with Unity and LibreOffice?"
date: 2012-07-16
forum: General Help
---

### Post by azangru on 2012-07-16
I wasn't quite sure in which section of the forum to post this. It's partly a help request, partly a rant, partly a curiosity to see how many people are affected. The bug seems to have appeared several days ago, most probably after the latest update (no ppas, no nothing, just a vanilla Ubuntu 12.04). It goes like this: I start a new Ubuntu session, and fire up Writer and some other programs (Firefox, Nautilus, Empathy, etc.). Everything goes fine until at some point the Writer's window can no longer be seen in the switcher, and in the dash the left triangle next to the Writer's icon disappears while the right triangle (which is supposed to indicate focus) remains constantly next to the Writer's icon despite the focus being on a different window.

So, Writer becomes very difficult to use: once you switch from Writer to a different window, you are lost. You can, of course, start minimizing all the windows that block the Writer's window or you can use Super+W, but Alt+Tab or clicking the Writer icon in the dash don't work.

The issue, I believe, is described in Launchpad [[COLOR="Blue"]_here_[/COLOR]]("https://bugs.launchpad.net/bamf/+bug/842566"). Apparently, it was an old glitch, but if you look in the end of the thread, you'll see it has re-emerged. At least there are now two of us (me and the Launchpad guy) who have been affected.

P.S.: I am not sure whether the glitch starts randomly or whether there is something that provokes it, but I tend to experience it if I first start Writer and then start VirtualBox. Ve-ery frustrating :(

---

### Post by enthusy on 2012-07-17
I have the same weird behavior with Writer icon in Unity launcher. I also do not have any PPAs installed and I'm using clean Ubuntu 12.04. 

I was working with Writer this morning, and it was doing just fine. After that, I updated Ubuntu and the problem started. My previous update of Ubuntu was done 5 days ago. So the problematic update that have created this problem should not be older than 5 days.

---

### Post by bobsan on 2012-07-17
I haven't experienced this in 12.04, but it used to happen in 11.04 until an upgrade fixed it (I use ppa). A work around before the update was to activate the quick start launcher, but before you do that make sure you go to dconf-editor and whitelist Libreoffice, or the quick launcher icon won't show on your upper panel. In older version of LibreOffice you need to quit it manually (by choosing quit from the icon, or from terminal of course but it is easier to use the icon)or you can't shut down or restart your machine.

---

### Post by philinux on 2012-07-17
Moved to General Help.

---

### Post by azangru on 2012-07-20
The problem seems to have gone after the latest update. I hope they've fixed it.

**UPDATE:** Ironically, it reoccurred just after I've posted this message. So I am afraid I was wrong - it's still there :-(

---

### Post by rtbarker on 2012-07-20
I have this problem on my desktop and my laptop, I first noticed it yeterday.

As a workaround, I installed the "lo-menubar" package and relogged. So far it seems to have fixed it and my menus are now properly integrated.

---

### Post by triclops200 on 2012-07-20
Also, it could be an issue with compositing, try turning it off while using libreoffice

---

