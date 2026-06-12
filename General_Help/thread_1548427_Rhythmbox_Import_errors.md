---
title: "Rhythmbox Import errors"
date: 2010-08-08
forum: General Help
---

### Post by gauravbutola on 2010-08-08
Suddenly my rhythmbox is showing a new tab that says "Import errors" I am attaching the screenshot of that error report.
and one major problem I have found out after that is rhythmbox contains non audio formats (like .iso and others) and rhythmbox tries to play these non audio files and make scratchy sounds. i dont know how come its reading these formats and it creates nuisance while the song changes and it tries to play those formats.

I am using Lucid Lynx.

---

### Post by gauravbutola on 2010-08-08
Bump

---

### Post by gauravbutola on 2010-08-08
plz someone help me on this

---

### Post by soldier1st on 2010-08-08
did you try to remove the offending file(s) from rhythmbox? by right clicking and remove them?

---

### Post by gauravbutola on 2010-08-09
> **soldier1st said:**
> did you try to remove the offending file(s) from rhythmbox? by right clicking and remove them?
those files are spread in my whole song list so its not possible for me to delete each one of them separately. 

plz someone give me a good solution.

---

### Post by nealmcb on 2012-05-01
I agree that Rhythmbox should be more discerning about what it tries to parse as a music file.  I'm not sure if there is a bug about that yet, but there should be.

In the meantime, you can investigate and document such problems via "debug mode" so they can be fixed, by starting the program up in debug mode like this:

 rhythmbox --debug > rhythmbox-debug.txt &

---

