---
title: "Cant Disable Navigation Toolbar"
date: 2010-05-12
forum: General Help
---

### Post by sedefsiz_masrapa on 2010-05-12
I am using Tiny Menu extension on my firefox so that I have to disable Navigation toolbar. I do so but everytime when I reopen the firefox I see that it is active again.
What can I do?
I am usinng firefox 3.6.3 on my ubuntu 10.04 machine(upgraded from 9.10).

---

### Post by gldearman on 2010-05-12
If changes to Firefox toolbar customizations are undoing themselves when you restart Firefox, you may have a corrupt file in your Firefox profile.

The Mozillazine Knowledgebase article on that problem, which includes directions on how to fix it, is [here]("http://kb.mozillazine.org/Corrupt_localstore.rdf").

---

### Post by lovinglinux on 2010-05-12
> **gldearman said:**
> If changes to Firefox toolbar customizations are undoing themselves when you restart Firefox, you may have a corrupt file in your Firefox profile.

The Mozillazine Knowledgebase article on that problem, which includes directions on how to fix it, is [here]("http://kb.mozillazine.org/Corrupt_localstore.rdf").

+1

If that doesn't work (probably will), then it could be another extension causing the problem. See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

BTW, I also use Tiny Menu and it's great.

---

### Post by sedefsiz_masrapa on 2010-05-13
hey guys, you are great! thank you. I solved by deleting that localstore.rdf file and uninstalling amazon extension.

---

