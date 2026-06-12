---
title: "Firefox displays pdf as text instead of asking to save or open."
date: 2010-11-11
forum: General Help
---

### Post by Mercedes300 on 2010-11-11
Hi all.

I have three machines running Ubuntu v.8.04 with Firefox v.3.6.

I'm having some trouble with an html file loaded from my hard drive.  It is a table of file names setup with ```
<a href="FILENAME.pdf">FILENAME</a>
``` -- file name is "index.html".

Loading the html file into Firefox v.3.6 displays the filenames with the links.  On two machines on this file server -- not using a web server (LAMP) -- the html loads and clicking on the links produces the Firefox pop-up "What should Firefox do with this file" dialog.  The files then open in Evince as intended.

On the third machine -- without any apparent changes in setup or environment -- index.html loads into Firefox.  However, clicking on the links streams unintelligible (at least to me) binary into the browser, bypassing the "What should Firefox do with this file" dialog.  

I've looked at MIME types for the failing machine in Firefox -- EDIT  |  PREFERENCES  |  APPLICATIONS and the entry for Content Type PDF document (application/pdf) action is set to "Always ask" like the other two machines.  And xdg-mime query default application/pdf reports "evince.desktop" which is as expected.

Something strange is happening here and I can't seem to isolate the variable.  Is there a way to force the dialog box to appear rather than just dumping the file contents into the browser?  Is there a way to add a MIME type in Firefox without clicking on a similar link -- which is all I can find on Firefox for how to correct this?

Any hints would be greatly appreciated.


Thanks.

---

