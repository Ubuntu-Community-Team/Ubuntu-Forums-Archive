---
title: "Missing folder icons in Firefox Bookmarks and other problems"
date: 2011-11-08
forum: General Help
---

### Post by Seb71 on 2011-11-08
I recently installed Ubuntu 11.10 (clean install). Using Unity 2D (my nVidia FX5200 card is blacklisted so it can not run Unity).

The icons for folders/subfolders from Firefox Bookmarks menu (the one from Global Menu - in the top panel) are missing. Icons for bookmarks are shown.

I erased my Firefox profile and made another one - no change.

I erased places.sqlite - no change.

Any ideas how to restore the missing icons?

----

Also, I can not drag and drop items from Bookmarks menu to rearrange them - is this by design or is a bug?

---

Third problem: middle click on a bookmark from Bookmark menu opens the link in the current tab instead of opening it in a new tab. Is this by design or a bug?

----
When opening the bookmarks in the Firefox sidebar, everything works as expected: the icons for folders are shown, I can drag and drop Bookmarks items to rearrange them and middle click on a bookmark opens the link in a new tab.

---

### Post by lovinglinux on 2011-11-09
> **Seb71 said:**
> The icons for folders/subfolders from Firefox Bookmarks menu (the one from Global Menu - in the top panel) are missing. Icons for bookmarks are shown.

I erased my Firefox profile and made another one - no change.

I erased places.sqlite - no change.

Any ideas how to restore the missing icons?

Installl DConf, launch it, go to "org >> gnome >> desktop >> interface" and tick the option "menus-have-icons". Restart Firefox.

> **Seb71 said:**
> Also, I can not drag and drop items from Bookmarks menu to rearrange them - is this by design or is a bug?


That seems to be an issue with Global menu. If you disable Global Menu Bar integration add-on in Firefox about:addons, then you can drag them. However, you lose the Global menu functionality.

> **Seb71 said:**
> Third problem: middle click on a bookmark from Bookmark menu opens the link in the current tab instead of opening it in a new tab. Is this by design or a bug?

Probably a configuration issue or a bug. Get an add-on like [Tab Utilities](https://addons.mozilla.org/en-US/firefox/addon/59961/) and configure it the way you want.

---

### Post by Seb71 on 2011-11-09
> **lovinglinux said:**
> Installl DConf, launch it, go to "org >> gnome >> desktop >> interface" and tick the option "menus-have-icons". Restart Firefox.

It works (but I installed dconf-tools / Dconf Editor).

> **lovinglinux said:**
> 
That seems to be an issue with Global menu. If you disable Global Menu Bar integration add-on in Firefox about:addons, then you can drag them. However, you lose the Global menu functionality.
So this is by design, not only on my PC. I prefer to keep the Global Menu in Firefox for consistency.

> **lovinglinux said:**
> 
Probably a configuration issue or a bug. Get an add-on like [Tab Utilities](https://addons.mozilla.org/en-US/firefox/addon/59961/) and configure it the way you want.
Installed the add-on. Did not make any change in the configuration. Now middle click opens in new tab.

Thank you.

---

### Post by lovinglinux on 2011-11-09
> **Seb71 said:**
> Installed the add-on. Did not make any change in the configuration. Now middle click opens in new tab.

I can confirm the issue. I tested and it happens only in Unity 2D. Please make a bug report on launchpad.

---

### Post by Seb71 on 2011-11-10
[Done]("https://bugs.launchpad.net/unity-2d/+bug/888418"). Thanks again.

---

