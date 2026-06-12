---
title: "Google Chrome open-maximized startup switch"
date: 2009-10-21
forum: General Help
---

### Post by wcGary83 on 2009-10-21
Hi all!

I can't seem to get the -open-maximized startup switch to work in
Chrome... Has anyone else had any luck?

Gary

---

### Post by fragos on 2009-10-21
Use double dash to start the option as in:
--open-maximized

---

### Post by wcGary83 on 2009-10-21
Thanks!

---

### Post by EdwardMorris on 2010-05-26
Can you please post the exact command, I've had no luck with this on Lucid.

---

### Post by fragos on 2010-05-26
/opt/google/chrome/google-chrome --open-maximized %U

---

### Post by EdwardMorris on 2010-05-27
This works when launching chrome the first time. Chrome seems to remember to launch maximized even without the switch, where it fails to start maximized is when you open a link in a new window or simply open a new window, it never starts the new one maximized. Any suggestions for that?

I looked around the launcher/wrapper to see if I can insert this option when it starts up a new window but not sure where would that be in the code.

---

### Post by fragos on 2010-05-27
You might try Edit Menus as I believe that may be what controls execution when you click on an .html file. There is also /opt/google/chrome/google-chrome.desktop.

---

