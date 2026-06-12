---
title: "LibreOffice issue"
date: 2011-01-12
forum: General Help
---

### Post by TakeitEZ on 2011-01-12
I downloaded Libreoffice through a PPA today (Ubuntu 10.10 -Asus Eee netbook) and it seemed to go smooth, but when I opened Libre I could not click on any of the different options (text document, spreadsheet, presentation, etc).  I can only click on the template and open buttons on the bottom of the screen.  I click the new document template via the template menu and still nothing happens.  What can I do to fix this issue?

---

### Post by TakeitEZ on 2011-01-12
Seems that I am not getting much of a reply for my problem.  Can someone please tell me how to purge LibreOffice instead and I can then try a reinstall.  Thanks.

---

### Post by The Cog on 2011-01-12
You should be able to find all the LibreOffice packages in synaptic package manager, mark them all for complete removal and apply.

I have installed LibreOffice from .deb packages downloaded directly from their web site and don't have that problem. I downloaded the .deb.gzip.bz2 file, unpacked it, opened a terminal in the DEBS directory and ran the command ```
sudo dpkg -i *.deb
```, same again in the desktop integration debs subdirectory.

---

### Post by CarpKing on 2011-01-12
You might not have to purge.  
[http://ubuntuforums.org/showpost.php?p=10350172&postcount=4](http://ubuntuforums.org/showpost.php?p=10350172&postcount=4)

---

### Post by TakeitEZ on 2011-01-13
Thanks for the replies, Carp and Cog! Before I saw both of your replies, I was able to purge libreoffice and reinstall it by installing the PPA repository for Libre and then install it through the Software Center.  It is working fine now.  I guess a Ubuntu noob like me should stick the Software Center to install apps until I have a better understanding of the Terminal and commands. :confused:  Again, thanks for the replies and insight.  :)

---

