---
title: "Installing Imagemagick"
date: 2010-10-24
forum: General Help
---

### Post by rugbert on 2010-10-24
So I installed imagemagick via apt-get so I could use paperclip (on Rails) to resize images but I cant get it to work. there is no command for imaagemagick after installation. So I cant get paperclip to resize anything.

Do I need something else installed?

---

### Post by ubudog on 2010-10-24
You can't launch it from Applications>Graphics?

---

### Post by rugbert on 2010-10-24
its not even showing up there. apt says its installed, but the command isnt being installed. So paperclip cant use it, and i cant run it at all.

---

### Post by gmargo on 2010-10-24
ImageMagick consists of mostly command line tools although there is a graphical interface named **display**.  The ImageMagick package does not include any **.desktop** files, which is where Gnome would look to generate it's menus.  So there is no entry for the **display** program in the main menu.  

You can run it from the command line or from the Debian menu or you can create your own launcher.

(To enable the Debian menu, install the **menu-xdg** package, then go to System->Preferences->Main Menu, and click the "Debian" box.  After that the **display** program will be visible in the menu under Applications->Debian->Applications->Graphics->ImageMagick.)

---

### Post by rugbert on 2010-10-24
im not trying to run it through the desktop. im tying to use it with paperclip, a ruby gem that facilitates file attachment to web forms. Paperclip uses imagemagick to resize images on upload.

But it needs the imagemagick to resize them, but there is not command to use! I just double checked /usr/bin and theres nothing.

---

### Post by gmargo on 2010-10-24
Use **convert** with the **-resize** option.  **convert** is part of ImageMagick.

---

