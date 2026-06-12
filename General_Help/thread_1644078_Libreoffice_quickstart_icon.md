---
title: "Libreoffice quickstart icon"
date: 2010-12-12
forum: General Help
---

### Post by Ivan.Calderon on 2010-12-12
Is there a way to change libreoffice's quickstart icon?

(Im not talking about removing it)

Just after installation, it had the libreoffice logo, after reboot it has the openoffice logo and a gray background (capture included).

[http://yfrog.com/08uglynp](http://yfrog.com/08uglynp)

Im using ubuntu 10.10 32 bits, libreoffice 3 rc1installed from debs and the orta theme (1.0)

---

### Post by Cherry Cotton on 2011-03-12
I think I have the same problem.

Do you use LibreOffice’s Human icon theme? What I’ve found is that one of the icons in there (“res/mainapp_16.png”, in “/usr/share/libreoffice/basis3.3/share/config/images_human.zip") still contains the OpenOffice logo, argh. I should file a bug about this... I don’t really know where, though.

What LibreOffice really should do is use the actual GTK functionality for showing the LibreOffice icon; I believe that would solve the gray background problem (as well as the fact that the icon is always 16x16 no matter what the panel’s size is, grrr).

Anyway! To answer your question, it looks like you can change that icon in that zip file, above, to whatever you want (so as long as it’s 16x16, I’d presume). I replaced the icon with the nearby “res/mainapp_16_h.png” (I think it’s called), which has the correct logo. Now LibreOffice has the right logo for the quickstarter icon.

The problems with this are: 1. I had to copy the archive to my home folder, modify it, and copy it back using sudo, which was a bit of a pain, 2. replacing the icon with another icon in the same folder within the archive manager is time-consuming, 3. it’ll all be overwritten the next time the libreoffice-style-human package is updated.

---

