---
title: "Ubuntu Remix 10.04: Suspend never recovers"
date: 2010-10-19
forum: General Help
---

### Post by gravyface on 2010-10-19
Have an LG x110 netbook that I've put Ubuntu 10.04 Netbook Remix on.  Works fine, except that 'Suspend' (whether closing the lid or choosing it from the shutdown options) never resumes correctly: I see the shell with "GLib-WARNING **: getpwuid_r(): failed due to unknown user id", but Googling around tells me that error is common and is usually hidden by the splash screen at boot.  

Shutdown -> Hybernate works fine, however, and if I could change the "close the lid" option to Hybernate I wouldn't bother with Suspend, but that doesn't appear to be an option.  

Any suggestions?

---

### Post by chessnerd on 2010-10-19
The option to switch the response to closing the lid is available, it just might not be out in the open. On Ubuntu (regular) the option is under Power Management Preferences ( System > Preferences > Power Management ), however, I don't think the netbook remix uses Gnome, so the option will likely be else-were. If it does use Gnome, but you can't find Power Management Preferences, try running gconf-editor and then going to Apps > gnome-power-management > actions (I think?).

---

### Post by gravyface on 2010-10-19
I found the Power Management settings, it's just that Hibernate is not an option in the drop-down: only Suspend, Shutdown, and Blank Screen.

---

### Post by chessnerd on 2010-10-19
Then you can try using the gconf-editor (Alt-F2, gconf-editor) and then going to apps > gnome-power-management > buttons and manually change the values under lid_ac and lid_battery to "hibernate" (without quotes).

---

### Post by gravyface on 2010-10-19
Ok, set lid_battery to "hibernate" (no quotes) and shut lid.  Waited a good 45 seconds, did not seem to be hiberating so I opened it up again and it said, "Computer failed to Suspend: Could not Hibernate".

---

### Post by chessnerd on 2010-10-19
Huh. I don't see why hibernating using the standard Shut down > Hibernate would be any different from hibernating when the lid is closed. I feel like there is probably a deeper, root cause that is not being identified here.

Well, you could always set the option to just blank the screen instead, but that hardly saves any power compared to suspending or hibernating...

---

