---
title: "Problem with ubuntu 9.04 and firefox 3.0.13"
date: 2009-08-29
forum: General Help
---

### Post by MastroLindo on 2009-08-29
Hi all.

I have a problem with my firefox after the update to 9.04.

The navigation bar seems bugged: I can write an address on it and go to the site, but it doesn't update the address whenever I click on a link, nor I can use the Back, forward, stop and reload buttons that are inactive.

Sometimes even my main menus (file, edit, view, etc) becomes gray.

I just had a couple of addons (downthemall and adblock plus) and I removed them to check if they were causing the problem.
I also tried to uninstall and reinstall again, trying to install both "firefox-3.0" or "firefox" packages.
Nothing changed.

I am using compiz and nvidia 1.80 display drivers, if that can be interesting for the solution, but even with compiz disabled I can't use the bar properly.

Help and suggestions are really welcome :) thanks to all


now that I see: bookmarks menu doesn't work either (I can't see any bookmark nor add new ones)

---

### Post by DeMus on 2009-08-29
> **MastroLindo said:**
> Hi all.

I have a problem with my firefox after the update to 9.04.

The navigation bar seems bugged: I can write an address on it and go to the site, but it doesn't update the address whenever I click on a link, nor I can use the Back, forward, stop and reload buttons that are inactive.

Sometimes even my main menus (file, edit, view, etc) becomes gray.

I just had a couple of addons (downthemall and adblock plus) and I removed them to check if they were causing the problem.
I also tried to uninstall and reinstall again, trying to install both "firefox-3.0" or "firefox" packages.
Nothing changed.

I am using compiz and nvidia 1.80 display drivers, if that can be interesting for the solution, but even with compiz disabled I can't use the bar properly.

Help and suggestions are really welcome :) thanks to all


now that I see: bookmarks menu doesn't work either (I can't see any bookmark nor add new ones)

When you uninstalled Firefox did you also delete the hidden folder in your user folder?
There is a folder called .mozilla in your home folder /home/username/.mozilla.
Rename that folder after uninstalling firefox. Then install it again and try again.
Success.

---

### Post by MastroLindo on 2009-08-29
Ok it worked, thanks man. Any ideas about what in my config folder could make that wierd thing happen? I never touched core Firefox config....

---

