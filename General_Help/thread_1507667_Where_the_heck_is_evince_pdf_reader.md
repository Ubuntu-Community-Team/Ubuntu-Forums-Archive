---
title: "Where the heck is evince pdf reader?"
date: 2010-06-11
forum: General Help
---

### Post by dderolph on 2010-06-11
I have Ubuntu 10.4LTS installed as a virtual machine in VMware Player. I recall from a previous installation of Ubuntu 9.04 or 9.10, a dual-boot installation with Windows, that Evince was on the Applications menu somewhere. Am I right about that?  

But, with this current installation of Ubuntu 10.4LTS, if I save a PDF from a website and then open it, it opens with Document Viewer 2.30.1. Is Document Viewer 2.30.1 actually Evince?  And, where is this PDF reader, whatever it's actually called, on the Applications menu or, if not there, why is it not there?  If this is normal, is there no way to open the PDF reader without first selecting a PDF file to be opened?  In other words, is it not possible to open the PDF reader and then use it's menu to browse to a PDF file and open it, just as I can with Adobe Reader or Foxit Reader in Microsoft Windows?

---

### Post by ucal on 2010-06-11
Open a terminal and type evince.  That opens it, and allows you to browse for pdfs through your file manager.  

You can create a shortcut for it, but I only know how to add those to the top bar, and not to the application menu.  

For the top bar shortcut, Right Click the top bar---->Add to Panel----> Custom application launcher.  The important bit is typing evince into the command area, title/name is just flavor.

Edit:  I'm pretty sure I didn't manually install evince, ergo it came with the starting set up, but just in case, running in a terminal:

sudo apt-get install evince

will install it, then you can do all the stuff above.

---

### Post by dderolph on 2010-06-11
Thanks for your reply. Apparently it's installed so I believe there's no need to install it.  It must be installed since it opens if I right click on a PDF file and select Open.  

I tried your suggestion for adding it to the Panel; I started Evince from a Terminal window but when I right clicked on the top bar, Add to Panel was not an option.  

So, evince remains an application which appears no where on the Applications menu or as a shortcut on the Desktop or as an a shortcut on the Panel.

---

### Post by star11786 on 2010-06-11
well i m new to ubuntu but what i have seen is that evince is renamed to document viewer.

in order to add it to application menu, right click on the menu and

Edit Menus --> Graphics --> check document viewer.

this will show document viewer in the menu under the submenu of graphics

---

### Post by dderolph on 2010-06-12
Thanks, star11786, that did the trick.

---

### Post by ucal on 2010-06-12
> **dderolph said:**
> Thanks for your reply. Apparently it's installed so I believe there's no need to install it.  It must be installed since it opens if I right click on a PDF file and select Open.  

I tried your suggestion for adding it to the Panel; I started Evince from a Terminal window but when I right clicked on the top bar, Add to Panel was not an option.  

So, evince remains an application which appears no where on the Applications menu or as a shortcut on the Desktop or as an a shortcut on the Panel.

I meant the top bar of gnome :D  Sounds like your problem got solved a better way though.  Glad it worked out.

---

