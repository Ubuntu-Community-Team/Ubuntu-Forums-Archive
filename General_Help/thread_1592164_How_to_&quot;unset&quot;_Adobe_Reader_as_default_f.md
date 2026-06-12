---
title: "How to &quot;unset&quot; Adobe Reader as default for PDF files"
date: 2010-10-10
forum: General Help
---

### Post by Ralph L on 2010-10-10
I normally use the Evince Document Viewer for .pdf files.  However, sometimes Adobe Reader is better.  I recently downloaded (the Linux version directly from the Adobe website) and installed Adobe Reader.  Somehow it set the default viewer for .pdf files to Adobe Reader.  Even if I right click on a .pdf document, select evince, and check the box to make evince the default viewer, the next time I click on a .pdf file Adobe Reader comes up.  Adobe must have set some configuration file to force Adobe Reader to be used.  Does anybody know how to change this, so Evince is my default document viewer again?

As an aside I am suspicious that Adobe plants some cookies or other bad stuff in my system and reports stuff back to Adobe.  Does anybody know if this is true, and if so, how I can get rid of this stuff.

Thanks
Ralph

---

### Post by linux4me on 2010-10-10
Did you also change the default application for PDFs in Firefox (Preferences -> Applications) back to Evince or Always Ask?

Is Evince staying the default application for PDFs in Nautilus once you change it? 

> As an aside I am suspicious that Adobe plants some cookies or other bad stuff in my system and reports stuff back to Adobe. Does anybody know if this is true, and if so, how I can get rid of this stuff.

I don't know about Acrobat Reader doing this, but supposedly Flash does leave cookies--Flash cookies, too--on your machine for settings and such.

---

### Post by gadolinio on 2010-10-10
First, I understand that you already tried right-clicking the pdf file, then going to properties, "open with" tab, and selecting evince as the default in the list of applications.
If you already did this, you could check the files mimeapps.list and mimeinfo.cache, both in /home/USERNAME/.local/share/applications.
Look for entries starting with "application/pdf="
For example 
application/pdf=evince.desktop;f-spot-view.desktop;firefox.desktop;AdobeReader.desktop;
Check for any entry application/pdf= stating that Adobe is the default. You might try replacing your entries with mine, after making a backup of both files just in case ;)
Good luck!

---

### Post by Ralph L on 2010-10-10
Thanks linux4me and gadolinio.  I did what each of you suggested and now I bring up evince when I double click a file.  I haven't tried opening with Firefox yet, but I think it will work.  I completely deleted Adobe Reader from mimeapps.list, but when I right click on a .pdf file and go to "Open with", Adobe Reader is still the first program listed.  This is fine with me, but it tells me that there is another configuration file at the operating system level that has Adobe Reader in it.

Anyway you guys solved it.
Thanks again

Ralph

---

### Post by gadolinio on 2010-10-11
> **Ralph L said:**
> when I right click on a .pdf file and go to "Open with", Adobe Reader is still the first program listed.

Does Adobe Reader appear in the list of right-click-->properties-->"open with" tab?
As far as I've seen, deleteing an application from there makes it stop appearing in the contextual menu.

---

### Post by Roo on 2011-04-29
I just ran into this problem myself on Lucid.

The file:
~/.local/share/applications/mimeapps.list

Contained:
```
[Added Associations]
application/pdf=AdobeReader.desktop;gimp.desktop;evince.desktop;
```

By changing it to be:
```
[Added Associations]
application/pdf=**evince.desktop;**AdobeReader.desktop;gimp.desktop;
```

Now evince starts by default, and AdobeReader is still an option in the menu.

---

