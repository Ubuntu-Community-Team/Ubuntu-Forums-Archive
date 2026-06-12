---
title: "import TT fonts hw?"
date: 2009-10-16
forum: General Help
---

### Post by ottosykora on 2009-10-16
How is the correct way of installing (importing) fonts into ubuntu?

Under Kubuntu I remember having some kind of fonatmanager helping here, but what is used in ubuntu for that?

---

### Post by ajgreeny on 2009-10-16
All the fonts you will use in Ubuntu are stored in two places.

1.  /usr/share/fonts
2.  ~/.fonts

I recommend you install them in the #1 location,  as if you install them to your /home directory they will not be accessible from another account on the computer.  

First make a folder to hold your custom fonts.

```
sudo mkdir /usr/share/fonts/truetype/customttf 
``` I am using customttf as an example.

Next open a terminal in the folder where you have a bunch of custom fonts and type the following:

sudo cp ./*.ttf /usr/share/fonts/truetype/customttf  This will copy the truetype font files to that folder.

Now that we have the fonts in the proper folder we need to install them in Ubuntu.  That is what the fc-cache command is for.

Open a terminal in your customttf folder and type the following:

sudo fc-cache -f -v

This will install the fonts so that your applications like OpenOffice and others can use them.

I hope this helps.

---

