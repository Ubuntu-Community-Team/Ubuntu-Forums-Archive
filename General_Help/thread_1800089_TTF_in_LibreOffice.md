---
title: "TTF in LibreOffice"
date: 2011-07-08
forum: General Help
---

### Post by BorisPlankton on 2011-07-08
Hello,

I am on Ubuntu Natty.

Put TTF in fonts folder as follows:
Alt-F2
'gksudo nautilus /usr/share/fonts/truetype' 
Run
Created new folder called 'MyFonts' and copied in
Closed down File Browser

On opening LibreOffice went to Character then fonts but do NOT see any of the fresh TTF fonts.

Something else I need to do?

---

### Post by searchfgold6789 on 2011-07-08
Reboot?

---

### Post by BorisPlankton on 2011-07-08
Sorry tried that.Should have put in post.
Thanks.

---

### Post by grahammechanical on 2011-07-08
Have you tried installing those fonts? Open the folder and select each font file and right click and select to open with fontviewer. Then click the Install Font button. It works for me.

Regards.

---

### Post by searchfgold6789 on 2011-07-08
[http://ubuntuforums.org/showthread.php?t=241196](http://ubuntuforums.org/showthread.php?t=241196)

---

### Post by BorisPlankton on 2011-07-08
> **grahammechanical said:**
> Have you tried installing those fonts? Open the folder and select each font file and right click and select to open with fontviewer. Then click the Install Font button. It works for me.

Regards.

No go I am afraid. 
Made no difference. I will now try the suggested thread.

---

### Post by BorisPlankton on 2011-07-08
> **searchfgold6789 said:**
> [http://ubuntuforums.org/showthread.php?t=241196](http://ubuntuforums.org/showthread.php?t=241196)

Done: fonts still do not appear in Libreoffice although as I read the below output, this seems to have 'refreshed'. I do find them by character - font in Libreoffice? About to give up.

psas@psas-P5Q-PRO:~$ sudo fc-cache -f -v
[sudo] password for psas: 
/usr/share/fonts: caching, new cache contents: 0 fonts, 4 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 6 dirs
/usr/share/fonts/X11/100dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 9 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap: caching, new cache contents: 0 fonts, 2 dirs
/usr/share/fonts/cmap/adobe-japan1: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap/gs-cjk-resource: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 2 fonts, 15 dirs
/usr/share/fonts/truetype/MyFonts: caching, new cache contents: 271 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/takao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/thai: caching, new cache contents: 54 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 21 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: caching, new cache contents: 17 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-kacst-one: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-khmeros-core: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-liberation: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-punjabi-fonts: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ubuntu-font-family: caching, new cache contents: 6 fonts, 0 dirs
/usr/share/fonts/truetype/unfonts: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/wqy: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 2 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/fonts/type1/mathml: caching, new cache contents: 1 fonts, 0 dirs
/usr/X11R6/lib/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/psas/.fonts: skipping, no such directory
/var/cache/fontconfig: cleaning cache directory
/home/psas/.fontconfig: cleaning cache directory
fc-cache: succeeded
psas@psas-P5Q-PRO:~$

---

### Post by BorisPlankton on 2011-07-09
OK Update - copied fonts out to folder within (user?) folder in home and as I install they appear in libreoffice. So in my case copy and installing to home\psas does the trick.
Solved. Even if I do not understand quite why or how.
Thanks for the help.

---

