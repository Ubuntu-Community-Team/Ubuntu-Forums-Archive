---
title: "Lucid Lynx Problems"
date: 2010-05-12
forum: General Help
---

### Post by charlesC8188 on 2010-05-12
I just upgraded to Lucid Lynx, everything went smooth until I went to check out the new "ubuntu software center" and tried to download a package. The system is telling me that my packages are broke. I attached screen shots so if someone could take a look it would be greatly appreciated.

---

### Post by QLee on 2010-05-12
Did you get the theme mentioned from a third-party repository?

If so, does your sources.list still include that repository (software sources)?

If it is commented out or missing, add it and reload packages files (Update Manager, check; synaptic, reload; CLI, apt-get update. Then try again to upgrade that package.

---

### Post by charlesC8188 on 2010-05-12
Yes I d/l the theme from Ultimate Edition Website. I tried removing the source but i still receive the error message. I tried auto-removing it from the terminal with sudo apt-get install -f. And i receive the same message.


and the second picture is what happens when i tried to go into the update manager.

---

### Post by QLee on 2010-05-12
[QUOTE=charlesC8188]Yes I d/l the theme from Ultimate Edition Website. I tried removing the source but i still receive the error message. I tried auto-removing it from the terminal with sudo apt-get install -f. And i receive the same message.


and the second picture is what happens when i tried to go into the update manager.[/QUOTE]

In my previous reply my advice did not include the word remove, don't know why you translated to that.

---

### Post by charlesC8188 on 2010-05-12
it wouldn't let me get that far... that's the error soon as i opened the update manager.

---

