---
title: "Crashing and Formatting problems in OpenOffice Writer 3.2"
date: 2010-12-16
forum: General Help
---

### Post by rootless on 2010-12-16
I can't believe this.

I'm running Ubuntu 10.10.

Everything seemed to be in order, but I started having problems with Openoffice- it started crashing randomly, usually within a minute of starting to edit a document.

I did a 

```
sudo apt-get purge openoffice.org-*

sudo apt-get install openoffice.org-gnome openoffice.org-writer 
```

Writer is really all I need. Anyway, the problem persists. Since I purged it, it seems not to crash while editing .odt files, but it always does with .doc and .rtf.

I've also noticed that when I select a block of text, and go to "format -> paragraph" and try to change the spacing of only that block to single or double, it changes the entire document. I have made sure that I am only selecting one block of text. It still changes the entire doc.

What happened? I've never had a problem with openoffice until now, and now all this at once. I can't believe this- right during finals. Just my luck.

This is Openoffice 3.2. Any help would be greatly appreciated.

PS: with some tweaking, I've managed to get OpenOffice to recognize that I only want to single-space one paragraph. It requires me to separate it from the above and below paragraphs with a blank line.

I suppose I'm missing a package... but that still doesn't explain the crashing.

---

### Post by Morgonte on 2011-08-03
No solution, I'm afraid. Instead I have a similar problem. OpenOffice 3.2 crashes when saving rtf files. Odt and doc is fine.
I run Ubuntu Studio 10.04.

---

### Post by Hagar Delest on 2011-08-04
Try the vanilla version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

You should also [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

Note that the RTF support is very poor in OOo. Even .doc support is better. But keep working in native ODF and export in external formats when needed only.

---

### Post by The Cog on 2011-08-04
I've been quite pleased with LibreOffice. 3.4.2 was released last week. It may be worth installing that.
[http://www.libreoffice.org/download/](http://www.libreoffice.org/download/)
[http://www.libreoffice.org/get-help/installation/linux/](http://www.libreoffice.org/get-help/installation/linux/)

---

