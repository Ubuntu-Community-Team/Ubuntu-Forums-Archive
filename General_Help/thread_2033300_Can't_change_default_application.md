---
title: "Can't change default application"
date: 2012-07-25
forum: General Help
---

### Post by Wayfar3r on 2012-07-25
I'm trying to set sublime to open text and code files. I tried changing all instances of gedit.desktop in 

~/.local/share/applications/mimeapps.list

and

/usr/share/applications/defaults.list

to sublime.desktop and even restarted. Still, no files open in sublime by default. I also tried adding the proper MimeTypes to the /usr/share/applications/sublime.desktop file in hopes that it would show open in nautilus' "open with" menu. Somehow, sublime is now the default text editor for txt but nothing else. Can't figure out what I'm doing wrong here... I'm trying to open .cc and .h files in sublime.

Using Ubuntu 12.04

---

### Post by HoCo xXSamXx on 2012-07-25
Try this:

1. Right click any .txt file
2. Go to the "Opens With" tab
3. Set a new default

Tell me how that works out for ya!

---

### Post by Toz on 2012-07-25
/usr/share/applications/default.list should work. Double-check the file, you spelled **sublime.des[COLOR="Red"]l[/COLOR]top** wrong.

---

### Post by Wayfar3r on 2012-07-25
#-othanks Toz. That did the trick.

---

### Post by Maien on 2012-08-12
Hi, I followed the instructions in [http://www.technoreply.com/how-to-install-sublime-text-2-on-ubuntu-12-04-unity/](http://www.technoreply.com/how-to-install-sublime-text-2-on-ubuntu-12-04-unity/). But the last step, where I replaced all gedit.desktop to sumblime.desktop, didn't work. Gedit is still the default app. Also, sublime is not included in the other apps list!

---

