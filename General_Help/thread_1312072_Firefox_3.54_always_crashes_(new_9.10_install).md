---
title: "Firefox 3.54 always crashes (new 9.10 install)"
date: 2009-11-02
forum: General Help
---

### Post by UranUtan on 2009-11-02
Hi,

Ubuntu 9.10 x32 fresh install + run system update.

After that, Firefox 3.54 crash constantly. Trying to run in terminal by "firefox -safe-mode" disabled everything with no results. Also remove + reinstall firefox either via Synaptic or sudo apt-get. Same results:

Either Firefox crashed after a few seconds (browser not having time to show up). Or When the the browser shows up, as soon as there is an action (Clicking Edit / Preferences, Clicking Tools/Add Ons, or open any URL and hit Enter), then Firefox crashes and closed itself.

I also have deleted the /home/user/.mozilla folder and restart firefox. Same issue. Doing system update, restart computer, etc doesn't solve the problem.

Can any one confirm? Or if you know what is going on, I would appreciate to benefit from your advices.

Thanks in advance.

---

### Post by UranUtan on 2009-11-05
UPDATE: I have installed:
- Opera 10: works OK

- Chromium: also crashed. But this time only on pages having flash.

So it was probably the adobe flash plugin. It was installed by a download from adobe site and manually installed. When trying to uninstall / remove, it always failed at the end and rollback (something corrupted or missing, don't remember the exact error message). In other words, I cannot remove adobe flash from the computer.

Then I redo a complete re-installation of Ubuntu 9.10 x32. As expected, Firefox works OK without the flash plugin. I will add it later. This time using the Ubuntu Software Center. Hope that will work.

EDIT: confirmed. Crash issue disappears if flash plug in is installed via Ubuntu Software Center.

---

