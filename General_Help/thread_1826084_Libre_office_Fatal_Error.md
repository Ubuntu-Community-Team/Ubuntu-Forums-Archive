---
title: "Libre office Fatal Error"
date: 2011-08-16
forum: General Help
---

### Post by dodgyphil on 2011-08-16
Hi all,

I have a libre office issue, I tried to start libre office impress and it appeared to start on click but did not load. This seemed to be the case with all the other libre applications. So I did an apt-get update, then ran an update now libre office applications give me a ("Fatal Error" The application cannot be startred [contex="user"]caught unexpected exception!).

IS this repairable? do I uninstall through synaptic and reinstall?

All help gratefully accepted.

Phil D

---

### Post by frncz on 2011-08-16
I also recently have problems with Libreoffice, both with 3.3.2 and 3.4. Weird crashes when I open .doc files, or save to .doc.
Problems do not appear when using Libreoffice 3.3 in Windows XP in a VirtualBox, but are there in Natty.

---

### Post by dodgyphil on 2011-08-16
Ok this fixed it for me.

Go into home folder show the hidden folders (Ctrl-H).I moved the .lbreoffice folder to a backup location. Then just restart an libreoffice application and it will make itself a new .libreoffice folder everything works again.

It worked for me nothing appears lost, hope it assists others.

Cheers
Phil

---

