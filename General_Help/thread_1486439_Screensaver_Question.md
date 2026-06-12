---
title: "Screensaver Question"
date: 2010-05-17
forum: General Help
---

### Post by sports fan Matt on 2010-05-17
If I wanted to put a screensaver up that is of a picture that I have (in my pictures folder), which directory would I gksudo nautilus to enable root access and have the screensaver picture as a choice when putting the pc in hibernation mode?

---

### Post by ubunterooster on 2010-05-17
screensaver+hibernation?!?

---

### Post by teh603 on 2010-05-17
Yeah, in Hibernate the "screensaver" is to turn the screen off.

For desktop pics, I believe its /etc/background , but you'd better manually browse there in Nautilus because I might have misspelled it or something. You'll also need to allow read/write to all users in the file permissions.

---

### Post by sports fan Matt on 2010-05-17
I'm looking in usr/share/screen & screen resolution and cant find anything.

---

