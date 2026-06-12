---
title: "Firefox display - text all overlaps"
date: 2009-08-17
forum: General Help
---

### Post by pickarooney on 2009-08-17
I get this problem on about 50% of websites - basically blocks of text and images all overlap one another making it ugly and sometimes unusable. My resolution is 1280*1024 on a 19 inch 4:3 LCD monitor and don't experience the same issue on an identical resolution/screen size on a(nother) Windows PC with FF. 

Attached is an example from [http://www.nanowrimo.org/](http://www.nanowrimo.org/)

How does this look to other people?

---

### Post by lovinglinux on 2009-08-17
It looks the same here.

The problem is that the text of the menu does not fit in the available space with your current font settings, so it bleeds out over the other elements of the page.

Go to Firefox Preferences, select the "Content" tab, click advanced under "Fonts & Colors", then reduce the value for "Minimum font size".

---

### Post by pickarooney on 2009-08-18
That certainly seems to have helepd on that particular site at least. Thanks muchly!

---

### Post by pickarooney on 2009-08-20
On a related, but slightly different note, how do the headlines on the site [www.lemonde.fr](www.lemonde.fr) look to other people?
To me, on both Firefox and Opera, the width of the font is not right - sometimes the vertical lines are too thin.

[http://www.lemonde.fr/ameriques/article/2009/08/20/obama-doit-faire-aboutir-la-reforme-de-la-sante_1230128_3222.html](http://www.lemonde.fr/ameriques/article/2009/08/20/obama-doit-faire-aboutir-la-reforme-de-la-sante_1230128_3222.html)

Here, for example, the headline looks like this (attached).

The right hand side of the As are all cut off.

---

### Post by stefcep on 2009-08-20
I did this:

I don't like the anti-aliased fonts on this screen, in both Vista and Ubuntu, they look blurry and give me a headache. I tried SegoeUI from vista with no anti-aliasing which looks OK in Vista but not so good in Ubuntu. So installed the Apple fonts from here:

[http://blog.taragana.com/index.php/archive/how-to-use-mac-fonts-on-ubuntu/](http://blog.taragana.com/index.php/archive/how-to-use-mac-fonts-on-ubuntu/)

-  * Open up a terminal by Applications->Accessories->Terminal
    * Copy/paste these commands:
      wget [http://ubuntu-debs.googlecode.com/files/macfonts.tar.gz](http://ubuntu-debs.googlecode.com/files/macfonts.tar.gz)
      tar zxvf macfonts.tar.gz
      sudo mv macfonts /usr/share/fonts/
      sudo fc-cache -f -v

Now the Mac Fonts are installed, if you like these fonts and want them to be the default gnome font, right click on your desktop and select Change Desktop Backround then click on Fonts, and you can customize your system fonts there.

Then System->Preferences->Appearance->Fonts

and set all my fonts to Lucida Grand 9 point, except window title to Lucinda Grand 10 point bold, with monochrome rendering and I am happy with it.

Right-click on the desktop and select Change Desktop Background-->Fonts-->Details:

96 dpi, no smoothing, hinting full.

I had to also configure Firefox: Edit->Preferences->Content->Fonts and Colors->Advanced->
everything to Lucida Grande 12, and deselect "Allow pages to choose their own fonts...".

Works well and looks very clean and readable.

No page rendering issues.

---

### Post by lovinglinux on 2009-08-20
> **pickarooney said:**
> On a related, but slightly different note, how do the headlines on the site [www.lemonde.fr](www.lemonde.fr) look to other people?
To me, on both Firefox and Opera, the width of the font is not right - sometimes the vertical lines are too thin.

[http://www.lemonde.fr/ameriques/article/2009/08/20/obama-doit-faire-aboutir-la-reforme-de-la-sante_1230128_3222.html](http://www.lemonde.fr/ameriques/article/2009/08/20/obama-doit-faire-aboutir-la-reforme-de-la-sante_1230128_3222.html)

Here, for example, the headline looks like this (attached).

The right hand side of the As are all cut off.

Mine looks fine. I'm using Arial font.

---

### Post by 4t0m1c_w07f on 2009-08-20
this may be the simplist solution but have you tried holding ctrl and scroll down? You might have accedentaly zoomed the browser..

---

### Post by pickarooney on 2009-08-20
> **lovinglinux said:**
> Mine looks fine. I'm using Arial font.

Ahh, i had ticked the option to allow websites to choose their own fonts.
After unticking it the text in some websites is still a bit big regardless of what I set the values to in the FF fonts preferences, but I can play around with that. Thanks!

---

