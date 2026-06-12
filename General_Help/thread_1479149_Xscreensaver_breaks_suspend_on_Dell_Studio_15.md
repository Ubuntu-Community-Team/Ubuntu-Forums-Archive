---
title: "Xscreensaver breaks suspend on Dell Studio 15"
date: 2010-05-10
forum: General Help
---

### Post by Mechaphoenix25 on 2010-05-10
Running Lucid Lynx Desktop 64-bit, clean install

I recently replaced gnome-screensaver with xscreensaver, using the following methods
[LIST]
[*]uninstalling gnome-screensaver
[*]installing xscreensaver
[*]having 'xscreensaver -no-splash' run at login through the default startup applications app
[*]to get gnome-do's lock to work: $ sudo ln -f /usr/bin/xscreensaver-command /usr/bin/gnome-screensaver-command
[/LIST]

Before I did these, suspend worked flawlessly, but now when I try to suspend, the screensaver comes up, freezes at a frame, the screen never blanks, and the computer never enters suspend.

Is there a way I can trigger a suspend without triggering the screensaver until after the resume?  Or change xscreensaver to not interfere with suspend?  I'd really like to have the screen come up locked after a suspend, but if a fix requires a non-secure suspend, I'd be willing to accept that.

My specs: Dell Studio 1558, Intel Core i5 M430@2.27GHz, 4GB RAM, ATI Mobility Radeon HD 4570 GPU on open-source radeon drivers (r600 chipset type).

---

