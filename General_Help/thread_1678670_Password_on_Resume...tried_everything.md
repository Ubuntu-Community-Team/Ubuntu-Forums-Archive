---
title: "Password on Resume...tried everything"
date: 2011-01-30
forum: General Help
---

### Post by jhiggy on 2011-01-30
Hello!  This is driving me sooo friggin nuts.  When I put my computer to sleep (suspend 3)  It ALWAYS asks for a password on resume.  I've removed the check box in the screen saver and in gconf-editor in the lock subsection and it still asks for it.  I have also commented out the section in acpi-support that says lock on resume.  I'm at wits end!  I'm running Ubuntu 10.10

---

### Post by InspiredIndividual on 2011-01-30
Maybe this is a very foolish question, but I'm going to ask anyway. Did you uncheck both check boxes in gconf-editor, lock_on_suspend and lock_on_hibernate? If not, did you uncheck the right one?

EDIT: you could also try to tick the checkbox use_screensaver_settings in gconf-editor:/apps/gnome-power-manager and untick the checkbox lock_enabled in gconf-editor:/apps/gnome-screensaver.

---

### Post by TheJackal12 on 2011-01-30
Ubuntu Tweak successfully disabled the password on resume for me.

---

### Post by Jummel on 2011-01-30
what about enabling automatic login on boot, and relogin on X restart?

---

### Post by jhiggy on 2011-01-30
> **Jummel said:**
> what about enabling automatic login on boot, and relogin on X restart?


Automatic login on boot is set, but I'm not sure about relogin on x restart? where do I find that option?

P.S.  Thanks everyone else for your input but I tried ubuntu tweak with no luck and all my lock check boxes are unchecked.

Edit:  It looks like this may be the key if someone can show me how to do it.  I just realized that it doesn't look like a typical Ubuntu lock screen, it actually looks like the normal "im starting up the computer for the first time" login screen.  Which is weird.  I also noticed it quits out of all my open programs on suspend as well....

---

### Post by jhiggy on 2011-01-31
Any ideas?

---

### Post by InspiredIndividual on 2011-01-31
I'm not sure if I can help you any further... Some ideas:

- install hibernate and try if it helps in your case

- if you have a swap partition: try suspend/hibernate from the LiveCD. If that doesn't work, try it from the LiveCD of an older Ubuntu version (if you've got any of them laying around).

You could also search the following thread for suggestions:
[http://www.uluga.ubuntuforums.org/showthread.php?t=1469340&page=20](http://www.uluga.ubuntuforums.org/showthread.php?t=1469340&page=20)

---

