---
title: "Different defaults for different applications?"
date: 2009-08-17
forum: General Help
---

### Post by owkaye on 2009-08-17
All I want is something that should be really simple:

I want kmail to open links in Firefox by default when I click on them ...

AND

I want File Browser to open files in Text Editor (gedit) by default when I click on them.

How do I set up my system so both of these things work under the same configuration?  Or is this impossible in Ubuntu 9.04?

---

### Post by oldos2er on 2009-08-17
Right-click on any text file, choose Properties, Open With, click Text Editor. 

 For Kmail, if you're running it in Gnome, you'll need the packages kdeartwork and systemsettings. Run systemsettings, Default Applications.

---

### Post by owkaye on 2009-08-17
Thanks oldos2er, you gave me the exact information I needed.

I am running kmail in gnome and after I installed the two packages you suggested it was a no-brainer to set the System Settings > Default Applications > Web Browser > Default Component to "Open http and https URLS in the following browser: Firefox"

This is a good lesson for everyone who runs kmail in gnome and wants web links to open in Firefox instead of gedit.  I've been living with the need to avoid clicking link  in email messages for months, and this fix is finally going to bring me back to using my computer the way I used to use it before Ubuntu.

Thanks again for sharing your knowledge, this is certain to make my life much better!

:)

---

### Post by sigixv on 2009-08-17
Check your system settings (more specifically default applications) and set firefox as default webbrowser to apply it system-wide. Normally you can also choose to either open a new window or a new tab in the browser.
If you use several webbrowsers, it might be possible to set the action within kmail preferences to use firefox as default to open it. I don't use kmail so i have no idea.


Edit: ok, glad you solved it:p

---

### Post by oldos2er on 2009-08-17
Well I also run KMail (and a bunch of other KDE apps) in Gnome; it took me awhile to figure things out e.g. setting fonts, etc. Everything's there in google, if you know where to look!

---

