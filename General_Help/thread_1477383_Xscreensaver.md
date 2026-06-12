---
title: "Xscreensaver"
date: 2010-05-08
forum: General Help
---

### Post by Sevy on 2010-05-08
Hi
Im using Xubuntu screensaver on Ubuntu but have a problem when I select this in system>preferences

                    Warning:
The XScreenSaver daemon doesn't seem to be running
on display ":0.0".  Launch it now?

How do I enable the Xscreensaver to launch on startup?

---

### Post by Xfce Lobby on 2010-05-10
My issue was that I had to click on xscreensaver and close it for it to initialize.  So I went into Applications>Settings>Xfce Settings Manager>Session and Start up>Application Autostart then Add
Name: Xscreensaver
Description: Xscreensaver restart
Command: xscreensaver-command -restart

I did this for each of my logins, Root then Desktop.

The settings were being saved, but not initialized so I found this to be the easiest.

Later.

---

### Post by Sevy on 2010-05-11
I added "xscreensaver" to startup applications which has also worked.
Some screensavers crash my system but have settled with ones that dont

---

### Post by Xfce Lobby on 2010-05-28
Initially this worked for my root, admin, and user logins with an automatic login of user. Since I changed user to require password on login the root started screen blanking and I cannot correct the root with this method. User and admin still work fine.  When I changed my hostname and only restarted and did not shut down all the way my user went to screen blanking, but a shut down corrected this.  Is there a file that processes on start in which I can add a similar xscreensaver command to allow my root to be included without an issue?  Or is X specifically set up not to run at root for security and I just hit a few null moments for my method to work? Any suggestions?

I say this because when I run VLC or update manager the screen blanking starts back up and I have to do a complete shutdown to eliminate this problem.  Do these programs start preconfigured areas that ignore my settings?

---

