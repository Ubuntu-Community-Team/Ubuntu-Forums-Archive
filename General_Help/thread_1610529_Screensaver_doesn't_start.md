---
title: "Screensaver doesn't start"
date: 2010-10-31
forum: General Help
---

### Post by wurlyfan on 2010-10-31
Hi there experts!

Recently I implemented the suggestion in this post ([https://answers.launchpad.net/ubuntu/+question/4443](https://answers.launchpad.net/ubuntu/+question/4443)), so that my screen would lock immediately upon start-up. I want to do this because my computer is in a shared living space yet must run continuously (to run ffuppes media server), and I don't want to leave it accessible to everyone.

The post suggests creating custom  versions of /usr/bin/gnome-locked-session and  /usr/share/xsession/gnome-locked.desktop, then selecting the "locked" session as the default start-up session.

Here are my versions of the two items (respectively):

#!/bin/bash
#beryl-manager
gnome-screensaver
gnome-screensaver-command --lock
exec gnome-session

[Desktop Entry]
Name=GNOME (locked)
Comment=This session logs you into GNOME and locks the screen immediately
Exec=/usr/bin/gnome-locked-session
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-2.0

This technique does indeed start a session with the screen locked, which is great. However, when I select the locked session at start-up. the screensaver no longer starts. I can lock the screen manually, but if I leave the computer without doing that, the screen will not lock automatically (because the screensaver doesn't start).

Using the original gnome session, the screensaver behaves normally (but anyone can gain access to the computer by rebooting it.  If I set a general password on my account, ffupes won't restart if the machine reboots (or is rebooted).

Can anyone suggest what might be happening, or how I might investigate further? I can't seem to open the default gnome-session script for comparison, but the gnome-locked-desktop file seems sensible compared with gnome-desktop.

Many thanks for any help to resolve this, or suggestions as to how I might leave my machine able to restart and run ffuppes automatically without becoming available to any passing person.

---

