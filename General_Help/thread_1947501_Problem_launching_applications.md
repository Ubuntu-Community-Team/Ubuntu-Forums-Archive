---
title: "Problem launching applications"
date: 2012-03-26
forum: General Help
---

### Post by Etnica on 2012-03-26
I am using Ubuntu 10.04 LTS and have a problem with launching applications.

I have created a second Firefox profile and with it, created a secondary shortcut of Firefox on my GNOME2 bar.

When I set the launching command for the new secondary shortcut as 'firefox -P Proxy -no-remote', its also setting the command for the original Firefox shortcut.
I have found that if I change the secondary shortcut icon to something other than firefox.png (which is what the primary shortcut is also using), then setting the launch command will not effect the primary shortcut... but this is not what I want. I want two shortcuts, using the official Firefox icon, the first starting up Firefox normally, the secondary launching another profile.

Does anyone know how I can fix this bug or use a work around?

---

### Post by Etnica on 2012-03-27
... bump.

---

### Post by lovinglinux on 2012-03-31
Try to create a new shortcut in your Desktop and give it the "Proxy" name instead of Firefox, then configure the command as you did, then drag it to the panel (i don't remember if you can do that in 10.04).

You could also set the default Firefox launcher as "firefox -P -no-remote", this will force it to open the profile manager, so you can choose the profile.

---

