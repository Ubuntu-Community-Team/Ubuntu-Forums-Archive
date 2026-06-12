---
title: "Startup Applications: Command does not run"
date: 2009-11-04
forum: General Help
---

### Post by mac9416 on 2009-11-04
Hi all!

When I create a startup item with Startup Applications (gnome-session-properties) using the following steps (designed to correct problems with computers booting up muted), the changes do not take effect on startup:

> 1. Run 'alsamixer' in the Terminal.
2. Get the settings where you want them and press Esc to exit.
3. Run 'sudo alsactl store 0' in the Terminal. You may get an error saying "Home directory X not ours." You can safely ignore that.
4. Run gnome-session-properties and click "Add". Put "Alsamixer Restore" into the Name blank, and "/sbin/alsactl restore" into the Command blank. Feel free to add a description if you like.
6. Click "Add" to finish making the startup item and click "Close" to exit gnome-session-properties.
7. Reboot and check the results!

**However, most people can't test that, so disregard it. This is the important thing:** I created a sanity-check startup item called "Startup Applications" with the command 'gnome-session-properties'. The program does not run at startup, so something is obviously wrong with either Startup Applications, or the way I am doing things.

Any ideas? Thanks in advance!

---

