---
title: "Inkscape update dependency problem"
date: 2011-10-08
forum: General Help
---

### Post by hawthornso23 on 2011-10-08
After a recent update to a natty system inkscape shows up in update manager as having problems preventing it from being updated. Attempting to mark it for upgrade in synaptic gives

```

inkscape:
 Depends: libpoppler-glib5  but it is not installable
 Depends: libpoppler7  but it is not installable
 Depends: libwpd8c2a  but it is not installable
 Depends: libwpg-0.1-1  but it is not installable

```A quick search in synaptic shows that  

[LIST]
[*]libpoppler-glib5 is not in the repository. I see libpoppler-glib6 .
[*]libpoppler7 is not present. I see libpoppler13 !!!
[*] libwpd8c2a is not present. The closest I've got is libwpd-0.9-9
[*]libwpg-0.1-1 is not present. I have libwpg-0.2-2
[/LIST]
 It looks to me like yet another case of somebody being too eager to pull old library versions out of the repository and killing a bunch of dependent applications in the process. Also it looks to me like Inkscape might need an update. However amazingly Inkscape appears to work just fine. I'm not sure what is up with that, but since it does work, I am most reluctant to try uninstalling/reinstalling it to clear the dependency problem. Any suggestions? I suppose as everything is working OK one solution would be to do nothing and just ignore the annoying update dependency messages.

Edit: oops - accidentally clicked on [lubuntu] instead of [ubuntu]. Sadly there seems to be no way to fix this error by editing.

---

### Post by dino99 on 2011-10-08
maybe you need to deactivate some ppa(s), then update

---

### Post by hawthornso23 on 2011-10-08
Ah - thanks for the hint. I don't know why but I had a maverick-backport repository. I edited and renamed it natty-backport and the problem went away. How odd.

---

