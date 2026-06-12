---
title: "&quot;Open With Other Application&quot; window has multiple entries of the same application"
date: 2010-12-02
forum: General Help
---

### Post by na5h on 2010-12-02
Hi! I've got duplicate entries for almost every application in the "Open With Other Application" window you get when you right click on a file (Banshee Media Player even has 3). Not a big deal really, but is there some way to fix this? I'm using Ubuntu Maverick.

---

### Post by Joe of loath on 2010-12-02
I'm on Arch and have the same problem, I would hazard a guess at it being to with Gnome.

(I have 12 Spotify icons in the list... Something to do with WINE makes the problem worse)

---

### Post by mc4man on 2010-12-02
generally each one of those listings corresponds to a .desktop in either /usr/</usr/local>/share/applications or ~/.local/share/applications

You're free to remove any user created .desktops directly from the context menu or remove any not used ones from ~/.local/...
(the latest wine installs a boatload of .desktops to ~/.local/...

As far as listing due to installed apps, normally you'd need to remove the app to remove the listing. 
I guess in instances where an app installs multiple .desktops (like banshee has 3), you could remove unused ones, though probably best not to.

---

### Post by na5h on 2010-12-04
> **mc4man said:**
> generally each one of those listings corresponds to a .desktop in either /usr/</usr/local>/share/applications or ~/.local/share/applications

You're free to remove any user created .desktops directly from the context menu or remove any not used ones from ~/.local/...
(the latest wine installs a boatload of .desktops to ~/.local/...

As far as listing due to installed apps, normally you'd need to remove the app to remove the listing. 
I guess in instances where an app installs multiple .desktops (like banshee has 3), you could remove unused ones, though probably best not to.
Thanks! I found the apps in /usr/share/applications. Can I delete the extra (double) apps from this folder, or will it mess up my applications? Does anybody know? Why do the applications install multiple entries, by the way?

---

### Post by yetiman64 on 2010-12-04
> **na5h said:**
> Thanks! I found the apps in /usr/share/applications. Can I delete the extra (double) apps from this folder, or will it mess up my applications? Does anybody know? Why do the applications install multiple entries, by the way?

I would not recommend removing entries from /usr/share/applications (like Banshees for instance) as it may affect your application. Also the next time an application is updated the entries in this folder will likely be regenerated anyhow. The 3 entries for Banshee have different "Exec=" lines and each one therefore has different functions for that program to use. To see this copy them to your Desktop and open them with gedit (easy way is to drag the gedit icon from Applications > Accesories to your top panel then drag and drop the .desktop files onto this icon, you will then get to see the differences).

If a duplicate entry is from ~/.local/share/applications and has "userapp" (without the quotes) in the filename, it can safely be removed. 

With numerous Wine entries (not sure if this applies to you, but has been mentioned in the thread), I personally don't delete them but remove them to a "quarantine" folder in my home folder. That way if I find I need it later it can easily be restored.

---

### Post by na5h on 2010-12-06
Ok! Thanks for the answers!

---

### Post by mc4man on 2010-12-06
The 3 banshee .desktops each have a different launch command, I'd leave them and as mentioned any .desktop in /usr/share/.. alone.
Only the common use one for banshee is visible in your Applications - Sound & Video menu, the other 2 are device related launch commands

---

