---
title: "Karmic Koala ugly gdm bg fix"
date: 2009-12-20
forum: General Help
---

### Post by Big_tone on 2009-12-20
I really hated the ugly brown loading/login background in Karmic Koala so, I fiddled with things till I found a fix that works.  Hope this helps!

For those people just looking to replace the ugly brown background gdm screen: this is the most simple workaround.

first - open up a terminal and type: sudo nautalis then type your password when prompted and minimize terminal (you are now root in nautilis) and navigate to /usr/share/images/xsplash via the window that opened (this will allow you to rename and edit your xsplash background)

second - download or create a bg of your choice and save to the desktop.

third - make the name of this file the same as the one in usr/share/images/xsplash (in my case it was bg_2560x1600.jpg)

fourth - drag your new image into the xsplash folder (usr/share/images/xsplash), replace when it asks you too (good practice to backup originals) and WALLAH! No more ugly brown screen. Since the same image is used for splash screen and login screen, there will be no more brown.

You can also edit the white loading bar (with gimp or whatever) but, I like it as is.

---

### Post by bodhi.zazen on 2009-12-20
Yep, when the designed the new GDM upstream they did not preserve the ability to easily customize GDM. Hopefully the GDM developers will add some of the previous options back in to gdmsetup or similar real soon.

Until then you may also enjoy this thread :

[HowTO: Comprehensive Guide to Customising GDM and XSplash - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1333683")

---

### Post by thumbsoup on 2010-01-01
Thanks that worked great. I really didn't like that ugly login screen.

FWIW, I believe the proper spelling is Nautilus?  

I got an error msg in the terminal, but it all worked fine anyway.

---

