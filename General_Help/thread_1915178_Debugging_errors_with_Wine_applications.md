---
title: "Debugging errors with Wine applications"
date: 2012-01-25
forum: General Help
---

### Post by rfkrocktk on 2012-01-25
I just finished installing Photoshop CS5 in Wine from an existing XP install. The only papercut is that a fatal error is thrown telling me that Photoshop needs to close, but it doesn't. Things basically work just fine.

However, I'd like to do a little bit of work and see if I can track down this issue and get rid of the dialog altogether to improve my competency in troubleshooting with Wine. 

My program log is here: [http://paste.ubuntu.com/817056/](http://paste.ubuntu.com/817056/)

There's a segfault in there somewhere, probably because I need to make a certain DLL native. Can anyone help me work backwards on this and find what the problem could be?

---

### Post by Cheesemill on 2012-01-25
You say you tried installing it from an existing Windows installation.

What happens if you run the installer through wine instead?

---

### Post by rfkrocktk on 2012-01-25
Installer crashes :)

---

### Post by Cheesemill on 2012-01-25
Have you read all of the info here:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158)
[]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158")

---

### Post by rfkrocktk on 2012-01-25
Yeah, I'm on version 11.10 amd64.

I followed that guide exactly. I'm just glad that Photoshop works, but I'd like to improve the usability a little bit if possible by getting rid of that error message. I'm also seeing weird alignment issues with windows, they often align to the top-left instead of being in their natural position.

---

### Post by rfkrocktk on 2012-01-25
Running ```
winetricks nocrashdialog
``` fixed that issue, but I'm still trying to figure out the top-left window alignment issue. I'd like to try and make it as natural as possible :)

You can see an example of what I'm talking about with the top-left alignment issue here: [http://askubuntu.com/questions/98574/oddities-in-photoshop-window-centering](http://askubuntu.com/questions/98574/oddities-in-photoshop-window-centering)

---

