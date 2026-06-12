---
title: "gDesklets and Maverick"
date: 2010-10-06
forum: General Help
---

### Post by geudrik on 2010-10-06
```

$ sudo apt-get install gdesklets

```

Yields...
```

Unpacking gdesklets (from .../gdesklets_0.36.1-4_amd64.deb) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-icon-theme ...
Processing triggers for shared-mime-info ...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up gdesklets (0.36.1-4) ...
/usr/lib/gdesklets/sensor/Sensor.py:82: SyntaxWarning: assertion is always true, perhaps remove parentheses?
  assert(self.__id, "The ID is invalid in the constructor.")


```
 and 
```

$ gdesklets start

== yields ==

Nothing. Get the little spinny 'I'm thinking' icon, and then nothing happens.


```

Any Ideas? I've seen a debian package floating around, and tried the manual install of that (which seemed to help a few people) but then it just sits trying to connect to the daemon, which is never found. :s

Maverick is quite nice, I do rather enjoy it over the LTS, but I miss my desklets.  /sigh

---

### Post by LPK on 2010-10-07
Try changing /usr/lib/gdesklets/utils/ErrorFormatter.py
Line 116

Original:
def _new_imp(name, globs = {}, locls = {}, fromlist = []):


Cange to:
def _new_imp(name, globs = {}, locls = {}, fromlist = [], test = []):

---

### Post by geudrik on 2010-10-08
You sir, are wonderful. ++ goes to you.

Topic Solved.

Edit: I'd +rep you if I could find the button... :s

---

### Post by Kyjan on 2010-10-09
Because I am always looking to learn, I'm curious to know why exactly this change worked to start gDesklets.  I too was having this problem.  Was it knowledge of the language that told you this was the problem?

I'm trying to start using Linux, and as a programmer, my analytical mind is trying to sift through the "how to do something and why" questions.

Thanks!

Kyjan

---

