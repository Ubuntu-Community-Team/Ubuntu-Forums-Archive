---
title: "cannot un-associate pdfs from acroread"
date: 2011-09-22
forum: General Help
---

### Post by RyanGT on 2011-09-22
I installed Adobe Reader with the install script from Adobe's website.  No matter what I do, I cannot associate pdfs with evince again.  I can right click and choose "open with", but double clicking always opens in acroread.  I tried right clicking and choosing evince and checking the remember this application box.  I also tried /usr/bin/evince as a custom command and checking the remember box.  Neither of these worked.  I also tried adding this line

evince:application/*

to /etc/mailcap.order

Nothing is working.

I even considered uninstalling acroread, but I don't know how to do that apart from deleting all directories and files associated with it.

Ryan

---

### Post by pablo7 on 2011-09-23
I tried to reproduce this, but didn't experience any problems.  What program(s) are you trying to open up PDF's in?

I used the Nautilus file manager and "Open with" the Evince document viewer worked just fine.  You probably should uninstall Adobe Reader and re-install it from the Ubuntu Software Center to see if that fixes things.  I found some instructions for uninstalling by digging down into the /tmp directory where the binary program had extracted the files.

From the Readme.htm file: 

"2.(d) In case of tarball or bin installer:

Run the following command:

<reader_install_dir>/bin/UNINSTALL"

I opened the terminal and typed:

sudo /opt/Adobe/Reader9/bin/UNINSTALL

and got:

Adobe Reader has been successfully removed from your system


Good luck!

---

### Post by Zill on 2011-09-23
RyanGT:  To reassign your default "open-with" application *do not* just select the required app when opening the file.

Instead, select an appropriate file in Nautilus, then select Properties from the drop-down menu.  Go to the "Open With" tab and add your desired application to the list if necessary.  Then ensure that your chosen app is selected.  Close the Properties window and this should have reset your default app as required.

---

