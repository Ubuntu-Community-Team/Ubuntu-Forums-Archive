---
title: "How to remove shutdown options from main menu."
date: 2009-10-09
forum: General Help
---

### Post by iamyourdemize on 2009-10-09
I want to remove the Lock Screen, Log Out, and Shutdow from the main menu. And on a side note, is there a way to remove the Clear Documents portion from the Places menu? A remember trying to do it a while back but was told there was no way to remove it....only to disable it.

---

### Post by VCoolio on 2009-10-09
Open gconf-editor, navigate to apps > fast-user-switch-applet and uncheck the show_session_commands box.
About the clear documents I don't know.

---

### Post by iamyourdemize on 2009-10-09
> **VCoolio said:**
> Open gconf-editor, navigate to apps > fast-user-switch-applet and uncheck the show_session_commands box.
About the clear documents I don't know.

I found suppress_logout_restart_shutdown under apps/indicator session. I checked it but that didn't make any difference.

---

### Post by iamyourdemize on 2009-10-10
I also forgot to mention that I am running 9.10. It wasn't there initially but only after I deleted the original shutdown applet and added a different one to the panel.

---

### Post by dj-toonz on 2009-10-10
I use a software Package called Ubuntu-Tweak to disable them & theres more to it aswell
 
you can disable loads of things & if you don't like that changes, you can always revert back to how it was before you enabled them & yes it does work under 9.10 As that's what I'm using

---

