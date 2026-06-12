---
title: "Installing Openoffice (not libre) on Oneiric"
date: 2011-10-18
forum: General Help
---

### Post by gregalynch on 2011-10-18
I've been getting a lot of really frustrating behavior from libreoffice writer the last few days on Oneiric.  First it would take forever (maxing out the cpu) when trying to open .doc files.  Now it won't open these at all, and only sometimes will open .docx files.  There are also a number of problems with its integration into Unity (sometimes I can't minimize or close, sometimes the launcher button doesn't work, etc.)

I never had any of these problems when I ran openoffice on Maverick.  Is there a way to go back to that version on Oneiric?  Its getting to the point where I can't do my work.

---

### Post by scottbomb on 2011-10-18
What drove me crazy was when I uninstalled LibreOffice then proceeeded to install OpenOffice, instead of installing OpenOffice, it installed LibreOffice again!

I found this and it works:

[http://www.ubuntugeek.com/how-to-install-openoffice-3-2-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-openoffice-3-2-in-ubuntu.html)

---

### Post by gregalynch on 2011-10-18
I did this (although I think I might have ended up with version 3.3 somehow - the folders and files had slightly different names, so I changed that in the terminal commands - but I don't think it worked.  I can't figure out how to launch the program.

---

### Post by vasa1 on 2011-10-18
> **gregalynch said:**
> I've been getting a lot of really frustrating behavior from libreoffice writer the last few days on Oneiric.  First it would take forever (maxing out the cpu) when trying to open .doc files.  Now it won't open these at all, and only sometimes will open .docx files.  There are also a number of problems with its integration into Unity (sometimes I can't minimize or close, sometimes the launcher button doesn't work, etc.)

I never had any of these problems when I ran openoffice on Maverick.  Is there a way to go back to that version on Oneiric?  Its getting to the point where I can't do my work.

No recent experience with .doc or .docx, but regarding "There are also a number of problems with its integration into Unity (sometimes I can't minimize or close, sometimes the launcher button doesn't work, etc.)" my experience is quite satisfactory.

I'm using LibreOffice 3.4.3 on 11.10.

---

### Post by scottbomb on 2011-10-19
> **gregalynch said:**
> I did this (although I think I might have ended up with version 3.3 somehow - the folders and files had slightly different names, so I changed that in the terminal commands - but I don't think it worked.  I can't figure out how to launch the program.

Yes when running the commands, the names will be slightly different as the page was written when the version was slightly earlier. After the installation process, make sure to create the start menu entries. I did this from within Thunar. I opened the installation folder that was extracted, then the DEBS folder, then "desktop-integration" and then double-click the only .deb file inside. That should open in your Software Manager program. Click install and it will set up all the menu items so you can then launch the programs.

---

### Post by gregalynch on 2011-10-19
I think I've tracked down the problem a little more - I thought it was the microsoft file format, but apparently it was the user-defined styles I had saved in the documents I was trying to open.  Libre does seem to be working on all the other .doc and .docx files now.

---

