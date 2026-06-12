---
title: "Upgrade to 10.4 and Openoffice 3.2"
date: 2010-05-17
forum: General Help
---

### Post by popsz on 2010-05-17
I upgraded to 10.4.  It crashed just before the clean-up but for all intent and purposes, 10.4 is installed.

Everything works fine except Openoffice.  Did not have this before the upgrade. 
Look below. I can't tell what font, font size and the menu is unreadable.  So far I only have this happening with Openoffice.  I completely removed it and reinstalled it.  Any ideas?

[IMG]http://www.primelineindustries.com/tools/weirdlook.png[/IMG]

---

### Post by scouser73 on 2010-05-17
Did you also remove the OpenOffice profile?  This cam be found by going to your home folder **~/home/username/.openoffice.org**

Delete that folder and restart OpenOffice.

---

### Post by popsz on 2010-05-17
Thanks for getting back to me.

Yes, I did remove the .openoffice.org from my home directory even before I reinstalled everything and before I ran it for the first time after the install. 

I removed it all first using synaptic package manager and marked everything for complete removal.  I removed almost everything.  hyphenation, hyphenation-en, pdfimport, thesaurus-en-us, help-en-us, l10-common, .org, base, base-core.

---

### Post by popsz on 2010-05-18
I found that after complete removal of everything pertaining to OOo3.2 and deleting the .openoffice.org profile from my home directory then downloading the Sun version of debs installing those and rebooting, the problem was gone.  This was at the suggestion of the community at openoffice.org.  
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

This can be tagged as solved.  Thanks! :)

---

