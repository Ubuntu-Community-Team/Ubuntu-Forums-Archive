---
title: "Creating Package (.deb) without source"
date: 2010-03-03
forum: General Help
---

### Post by Enf` on 2010-03-03
Hello all, Is there a guide on creating a package from PHP scripts or something? Example: if I've developed a system and I want to make it to a deb file to deploy to my friends and such. I've tried looking for one but I have not been lucky so far. Any helps or advice would be great. Oh, is it possible to specify a different path for installation too? Thanks.

---

### Post by gmargo on 2010-03-03
"How to make a "Basic" .deb": [http://ubuntuforums.org/showthread.php?t=910717](http://ubuntuforums.org/showthread.php?t=910717)

---

### Post by Enf` on 2010-03-05
Thanks for the reply. I'm curious about another thing now. How do I trace the version I've installed and compare it in the control/rules file to apply certain patch or equivalent to my configuration file?

---

### Post by Enf` on 2010-03-08
Hey guys, just another question. I've build a package successfully with pbuilder however another package of mine gives error. Both uses the same rule file (different path of course) but only one returns this error. Any idea what's happening? Thanks.

> mkdir: cannot create directory `/opt/mypackage-2': Permission denied

---

### Post by Enf` on 2010-03-16
Anyway, I guess I've fixed that issue. The second package depends on a few other libraries and needed the option to create directories in them and that was the cause of it. However, I've got another set of problem / question now. How do I go about sending updates to the package I've created. For example, I run certain upgrade scripts via 'php upgrade-file.php' to load changes to it. Is there a smart way to get it sorted in Ubuntu's packaging system? Or I need to find it manually? I hope someone could help me out here. Thanks.

---

