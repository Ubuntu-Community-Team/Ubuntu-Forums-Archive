---
title: "Reinstall unistalled packages?"
date: 2011-02-10
forum: General Help
---

### Post by ~Middle on 2011-02-10
Hello, i accidentally removed about 100 packages (long story) and i can see all of them in my Ubuntu software center history, is there anyway i can export that list of removed packages, and re-install them?

Thanks

---

### Post by ~Middle on 2011-02-10
Bump!

---

### Post by thefasterblueone on 2011-02-10
You can copy the text from System> Administration> Log File Viewer> dpkg.log and pick the date you made the deletions. 

As for reinstalling try apt-get update , apt-get upgrade , or you might have to install some manually.

---

