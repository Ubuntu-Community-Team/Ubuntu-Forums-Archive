---
title: "Firefox broken after update HELP!"
date: 2010-06-29
forum: General Help
---

### Post by w1av on 2010-06-29
Hi,

After doing a routine update the update manager crashed with an error....I noticed my Firefox icon had disappeared too! When I tried to see about re installing firefox I couldnt...here is the error I got:

[COLOR="Red"]E: /var/cache/apt/archives/firefox-branding_3.6.6+nobinonly-0ubuntu0.8.04.1_i386.deb: trying to overwrite `/usr/share/pixmaps/firefox.png', which is also in package firefox-2
E: /var/cache/apt/archives/firefox_3.6.6+nobinonly-0ubuntu0.8.04.1_i386.deb: trying to overwrite `/usr/share/bug/firefox/presubj', which is also in package firefox-2[/COLOR]

I don't know what to do. There are alot of Firefox-related items in the Synaptic package manager and I tried to uninstall but no use.....I keep getting the same error. HELP please!!!

---

### Post by chrisccoulson on 2010-06-29
> **w1av said:**
> Hi,

After doing a routine update the update manager crashed with an error....I noticed my Firefox icon had disappeared too! When I tried to see about re installing firefox I couldnt...here is the error I got:

[COLOR="Red"]E: /var/cache/apt/archives/firefox-branding_3.6.6+nobinonly-0ubuntu0.8.04.1_i386.deb: trying to overwrite `/usr/share/pixmaps/firefox.png', which is also in package firefox-2
E: /var/cache/apt/archives/firefox_3.6.6+nobinonly-0ubuntu0.8.04.1_i386.deb: trying to overwrite `/usr/share/bug/firefox/presubj', which is also in package firefox-2[/COLOR]

I don't know what to do. There are alot of Firefox-related items in the Synaptic package manager and I tried to uninstall but no use.....I keep getting the same error. HELP please!!!

Please uninstall the firefox-2 package and try again. firefox-2 has been obsolete for ages now, so you probably shouldn't be using it anyway

---

### Post by techunit on 2010-06-29
Why are you using firefox version 2 it shipped with version 3 beta... Um ok do this. In the terminal type the following

```
sudo aptitude purge firefox-2
``` you will lose your bookmarks so It may help to back them up.

```
sudo apt-get install firefox-3.0
``` sorry but not sure if you can get anything higher than 3 with out upgrading to a more recent release of ubuntu or using a ppa.

---

