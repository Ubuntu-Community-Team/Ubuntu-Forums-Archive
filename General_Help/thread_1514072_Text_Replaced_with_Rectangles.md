---
title: "Text Replaced with Rectangles"
date: 2010-06-20
forum: General Help
---

### Post by ardyer on 2010-06-20
So I booted up lucid lynx this morning and all the text is replaced with rectangles.  This is true for the login screen and any applications I can get to open (Some such as Chrome and Firefox will not launch).  If I boot into recovery mode and enter the command line, text works as normal.

I found some suggestions to run "sudo fc-cache -f -v" which did not fix the issue and one suggestion to edit xorg.conf in a particular way, but since xorg.conf doesn't exist in lucid lynx, that was a no go.

I did get a couple of screen shots:
[IMG]http://dl.dropbox.com/u/6187648/Screenshot%201.png[/IMG]
[IMG]http://dl.dropbox.com/u/6187648/Screenshot%202.png[/IMG]

---

### Post by gdonwallace on 2010-06-20
Check your locale settings.

If you want to do this from the command line, it is stored in /etc/default/locale and /etc/environment.

For English, it should be en_US.UTF-8

---

### Post by ardyer on 2010-06-20
> **gdonwallace said:**
> Check your locale settings.

If you want to do this from the command line, it is stored in /etc/default/locale and /etc/environment.

For English, it should be en_US.UTF-8

After checking those files, it was already set to en_US.UTF-8 so this didn't fix it :confused:

---

### Post by ardyer on 2010-06-20
Well, I tried reinstalling, which fixed the text.

The touchpad doesn't work anymore, but the text is fixed.

---

