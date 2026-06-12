---
title: "Window Manager broken."
date: 2010-07-28
forum: General Help
---

### Post by nullvariable on 2010-07-28
Over the last couple of weeks I experienced an occasional issue with not being able to switch windows. I blamed it at first on the batteries in my mouse. Now I've discovered that I can't alt-tab between windows either and the problem has become chronic. I've tested with different keyboards and mice to no avail. My system is basically fubar since I can only have one window open at a time and can only use keyboard shortcuts to operate it. Often the mouse (which still wanders around the screen under my control) is able to click things inside the pidgin window which loads when I first boot up but if this window is closed I can't use the mouse to click or scroll at all. If I could alt-tab then I'd assume it was a mouse issue but since I can't even do that I'm blaming the window manager. I've got 10.04 running upgraded from the update manager. I've run the most recent upgrades from apt-get via the command line but that didn't fix my issue.

Help?!

---

### Post by nullvariable on 2010-07-28
Two quick updates, switching kernels in GRUB doesn't appear to have any effect but using low graphics mode (which disables one of my monitors) appears to eliminate the issue.

Also I was able to operate between windows normally for a few seconds after the system loaded the last time I booted but only for a few seconds and then the problem continued.

---

### Post by dino99 on 2010-07-28
what you can try:

- clean the system with gconf-cleaner (yes to all) and bleachbit
- into synaptic: remove/purge then reinstall each gnome* packages installed (it will remove the meta-package ubuntu-desktop, dont worry reinstall it)

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by nullvariable on 2010-07-28
ran gconf-cleaner and bleachbit, rebooted same problem.

Reinstalled all the gnome packages, rebooted problem appeared to go away but came back. At first it was just missing clicks and for example clicking a panel icon would result in a right click action for a different item on the other side of the panel.

I also ran apt-get update, install and dpkg --configure, rebooted and still nothing.

I'm going through and trying to see what I've got running in the background that's different between safemode with one screen and regular mode with dual monitors that could cause the issue. It really seems to be something that's running after I login since for a few seconds everything seems to operate normally and then I lose the ability to move windows, alt-tab between them or otherwise change focus (without closing)

---

### Post by nullvariable on 2010-07-28
OK now the problem is following me into safe mode. At least I can still navigate around though. It's stalling between Google Chrome windows but right clicking on a panel and then clicking back the window in question seems to unstick it.

---

### Post by nullvariable on 2010-07-28
also happening in failsafe mode, dialog boxes from any application aren't clickable. You can tab to the button or use a shortcut key but they refuse to respond to mouse clicks.

---

### Post by nullvariable on 2010-07-28
It appears that while I believed the source of the problem to be elsewhere the issue was in fact Google Chrome. At first KDE seemed uneffected while Gnome freaked out all the time but it appears the latest update of Chrome did something because KDE started freaking out too. Switched back to Firefox and haven't seen the bug since.

Update:
removed the google-chrome-beta (sudo apt-get remove google-chrome-beta) and installed the stable version (sudo apt-get install google-chrome-stable) and haven't had a problem since.

---

### Post by nullvariable on 2010-07-28
Changing versions of Google Chrome did not in fact fix the issue. It appears that some sort of assistive technology was in play and this thread was what I needed to fix my issues: [http://ubuntuforums.org/showthread.php?t=1440048](http://ubuntuforums.org/showthread.php?t=1440048)

---

