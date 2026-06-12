---
title: "Headless Server Startup Problem"
date: 2010-05-03
forum: General Help
---

### Post by laka77 on 2010-05-03
Hello all,

I am running a headless server running Kubuntu that I just upgraded from 9.10.  Before the upgrade, I had the system set up to auto login, start an X session, and start VNC.  Worked great, but since the upgrade, I have two problems:

1) I can't get my KDE desktop to start up without a physical monitor plugged in.
2) The script I used to start VNC no longer works (started the script with under autostart in system settings menu).  There seems to be a problem with the -loopbg argument that keeps cycling VNC every second or so.  If I remove the -loopbg, the VNC server starts fine, but no longer listens after one VNC session.

Any ideas on how to fix these problems?

EDIT:

After some research, I decided to install ubuntu server edition instead of kubuntu desktop.  Now I forward X over ssh instead of using vnc.  Clean & easy (mostly).

---

