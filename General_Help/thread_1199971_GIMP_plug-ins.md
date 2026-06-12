---
title: "GIMP plug-ins"
date: 2009-06-29
forum: General Help
---

### Post by acefromspace on 2009-06-29
I downloaded a plug-in for GIMP (.zip) and can't extract it (no permissions) Only root can do this. Before, I used Fedora and would simply log in as root, but not sure how this works with Ubuntu... should I do this in terminal using sudo? What is the command line method to extraxt the zip file into /user/lib/gimp/2.0/plug-ins ? Also, my version of GIMP says 2.6.6 but the folder is named 2.0 Does this matter (there is another plug-in for older versions of GIMP) So far I love Ubuntu, but get confused about things that require root (I am used to Fedora) It seems some things are better done in terminal using sudo because I get no prompt for password when using graphical interface. No problem... I like using command line, just seems I must be missing something. BTW, the plug-in is for resizing images and converting to jpg. I could extract it to my home folder, but can't copy/paste into proper GIMP folder.

---

### Post by mcduck on 2009-06-29
Yes, you should use "sudo" when moving the files to correct place in terminal. Or, if you prefer doing it with graphical tools, run "gksudo nautilus" to open the file manager as root... ;)

Anyway, you can also install the plugin in your personal Gimp directory, ~/.gimp-2.6/plug-ins/

---

