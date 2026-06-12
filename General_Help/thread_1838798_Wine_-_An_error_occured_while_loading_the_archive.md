---
title: "Wine - An error occured while loading the archive"
date: 2011-09-04
forum: General Help
---

### Post by Fredhoud on 2011-09-04
:(Installed Wine + Winetricks - Ubuntu 11.04.
I get the following error message when I click on explorer, or try to insall any software: 
Archive:  /media/MSFP9/SETUP.EXE[/media/MSFP9/SETUP.EXE] End-of-central-directory signature not found.  Either this file is not a zipfile, or it constitutes one disk of a multi-part archive.  In the latter case the central directory and zipfile comment will be found on the last disk(s) of this archive. zipinfo:  cannot find zipfile directory in one of /media/MSFP9/SETUP.EXE or /media/MSFP9/SETUP.EXE.zip, and cannot find /media/MSFP9/SETUP.EXE.ZIP, period.

I have tried to install different version of Wine, with no success.  Any suggestion would be appreciated.

Fred Houd

---

### Post by Mark Phelps on 2011-09-04
What is "MSFP"? IF this is Front Page, then you're out of luck.  It won't work.  See the application compatibility page from the Codeweavers (Wine developers) site:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=15]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=15")

---

### Post by Fredhoud on 2011-09-04
Yes, Office 2000, FrontPage it was. Something interesting. I tried Crossover, after reading a few, and it works flawlessly. Everything works, even FrontPage!
Thanks,
Fredhoud

---

### Post by Mark Phelps on 2011-09-05
> **Fredhoud said:**
> Yes, Office 2000, FrontPage it was. Something interesting. I tried Crossover, after reading a few, and it works flawlessly. Everything works, even FrontPage!
Thanks,
Fredhoud

That's good news.  Please contact CodeWeavers and have them update their database, or login to their database yourself, and add an entry indicating that it works with Crossover.

---

