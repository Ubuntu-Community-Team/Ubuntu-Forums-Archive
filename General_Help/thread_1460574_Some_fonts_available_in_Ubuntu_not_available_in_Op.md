---
title: "Some fonts available in Ubuntu not available in OpenOffice"
date: 2010-04-23
forum: General Help
---

### Post by offbyone on 2010-04-23
I would like to use the Monospace font in OpenOffice Writer but I can't; the font is only available under System > Preferences > Appearance > Fonts. That's just one example; it looks like there are many more fonts available under the system fonts settings than in OpenOffice. Why is this? Am I jut seeing things or are there really less fonts in OOo than in the fonts settings?

---

### Post by labinnsw on 2010-04-23
Your fonts should be located in "/usr/share/fonts"
If you cannot find the one you want, [here is a good link to get some fonts.]("http://www.fonts4free.net/M19-download-fonts.htm")
Once you have your font, you can install it by opening it and installing from the font viewer.

---

### Post by fragos on 2010-04-23
Storing fonts in /usr/share/fonts or ~/.fonts will not make those fonts available until the font cache is rebuilt. This will happen after the next system boot or you can open a terminal window and run "sudo fc-cache -fv". After that the fonts will be available to application like OpenOffice and Gimp.

---

### Post by labinnsw on 2010-04-24
> **fragos said:**
> This will happen after the next system boot

I thought you only needed to restart the application. That is what worked for me in Hardy.

---

### Post by fragos on 2010-04-24
> **labinnsw said:**
> I thought you only needed to restart the application. That is what worked for me in Hardy.

Depending on the application it may initialize available fonts at startup which would mean it would need to be restarted as well.

---

### Post by Hagar Delest on 2010-04-24
Have copied fonts (Libertine tarball) in my ~/.fonts folder and they were immediately available for Mousepad and OOo, without any reboot. OOo was closed during the "installation" of course.

---

### Post by labinnsw on 2010-04-24
> **Hagar de l'Est said:**
> Have copied fonts (Libertine tarball) in my ~/.fonts folder and they were immediately available for Mousepad and OOo, without any reboot. OOo was closed during the "installation" of course.

I tried and confirmed this. I also tried pasting a font in /user/share/fonts and that also was immediately available when OpenOffice was opened without a reboot.

---

### Post by fragos on 2010-04-24
I see some things have changed from the past when running fc-cache was necessary. So many small improvements get made that we just don't know about. There was a time when you had to use CLI to setup many functions. Now so much is handled automatically. I rarely have to use CLI for configuration theses days.

---

### Post by Yogotiss on 2010-04-24
> **offbyone said:**
> I would like to use the Monospace font in OpenOffice Writer but I can't; the font is only available under System > Preferences > Appearance > Fonts. That's just one example; it looks like there are many more fonts available under the system fonts settings than in OpenOffice. Why is this? Am I jut seeing things or are there really less fonts in OOo than in the fonts settings?

you can try searching for fonts in the software center for open office or better yet install micrsoft office under wine.

---

### Post by fragos on 2010-04-24
OO seems to only use True Type fonts. There are a number of monospace TTF fonts with and without serifs. Chances are you already have "Freemono" and "NIMBUS mono". My favorite fonts are the DeJavu set based on Bitstream which include a sans-serif monospace font. You can use Synaptic to install "ttf-dejavu".

---

