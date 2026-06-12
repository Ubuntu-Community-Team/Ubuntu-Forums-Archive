---
title: "Open a file in terminal with a specific application"
date: 2009-10-25
forum: General Help
---

### Post by abq911 on 2009-10-25
I want to open a .xpi file in terminal with firefox, and the default in GNOME is Archive Manager. I want to open it in Firefox. I am a beginner with terminal, so try to go step by step. (The only command I memorized is cd:(:confused:)

---

### Post by Rinzwind on 2009-10-25
Open nautilus, find 1 of those extensions, right click that file, choose properties and the rest should be obvious ;)

---

### Post by abq911 on 2009-10-25
How can I do that in terminal then? I want this whole process to be in terminal, sorry if that wasn't clear enough.

---

### Post by P4man on 2009-10-25
you might try just launching

```
firefox ~/pathto/nameof.xpi
``` from a terminal

---

### Post by Rinzwind on 2009-10-25
> **abq911 said:**
> How can I do that in terminal then? I want this whole process to be in terminal, sorry if that wasn't clear enough.

Oh sorry I missed that :D

See the post above this one! That should be how.

---

### Post by diesch on 2009-10-25
I never did it, but [xdg-mime](http://manpages.ubuntu.com/manpages/jaunty/en/man1/xdg-mime.1.html) seems to be the way to go.

---

### Post by abq911 on 2009-10-25
> **P4man said:**
> you might try just launching

```
firefox ~/pathto/nameof.xpi
``` from a terminal

Thanks! Worked with me except it took me a while to figure out what the ~ does.

---

