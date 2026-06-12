---
title: "Fonts aren't installing !!!"
date: 2012-09-21
forum: General Help
---

### Post by uzumakifahim on 2012-09-21
I'm using Ubuntu 12.04. Not a very new user of Ubuntu, have installed a lot of fonts before. This time installing new font is really something different!!!

I have downloaded some True Type Font (ttf) fonts. Then paste them in the directory

```
usr/share/fonts
```

after that I've restarted LibreOffice writer but don't find them in the font list. No better result with PC rebooting.

Then again paste them in the directory

```
usr/share/fonts/truetype
```

and again restarted LibreOffice writer, but still they aren't on the font list.

I've tried in another way. Opened the fonts with font viewer and click on the "install" but the result is same. No improvement at all.

Finally I've created a folder in the directory

```
usr/share/fonts/truetype
```

and paste the fonts in the folder. And then run the following command in terminal

```
sudo fc-cache -f -v
```

No improvement at all. Output is here.

```
/usr/share/fonts: caching, new cache contents: 12 fonts, 5 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 4 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 9 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap: caching, new cache contents: 0 fonts, 2 dirs
/usr/share/fonts/cmap/adobe-japan2: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap/gs-cjk-resource: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/comfortaa: caching, new cache contents: 3 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 1 fonts, 17 dirs
/usr/share/fonts/truetype/Bangla font: caching, new cache contents: 8 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 13 fonts, 0 dirs
/usr/share/fonts/truetype/kacst: caching, new cache contents: 15 fonts, 0 dirs
/usr/share/fonts/truetype/kacst-one: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/lao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/liberation: caching, new cache contents: 16 fonts, 0 dirs
/usr/share/fonts/truetype/nanum: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/takao-gothic: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/tlwg: caching, new cache contents: 54 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bengali-fonts: caching, new cache contents: 13 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 21 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: caching, new cache contents: 17 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-khmeros-core: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-punjabi-fonts: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ubuntu-font-family: caching, new cache contents: 11 fonts, 0 dirs
/usr/share/fonts/truetype/wqy: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 2 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/fonts/type1/mathml: caching, new cache contents: 1 fonts, 0 dirs
/usr/X11R6/lib/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/fahim/.fonts: skipping, no such directory
/var/cache/fontconfig: cleaning cache directory
/var/cache/fontconfig: invalid cache file: 0373c9520c678ad3a7b51dcd8defd6a6-le32d4.cache-3
/home/fahim/.fontconfig: cleaning cache directory
/home/fahim/.fontconfig: invalid cache file: 0373c9520c678ad3a7b51dcd8defd6a6-le32d4.cache-3
/home/fahim/.fontconfig: invalid cache file: 6feb18a7eb53767e1fda8f70a925d3df-le32d4.cache-3
/home/fahim/.fontconfig: invalid cache file: c6336e1ef9a6d16129846299cdc925e8-le32d4.cache-3
fc-cache: succeeded
```

Very surprising and irritating issue indeed. Please help anyone.

---

### Post by FahadMKS on 2012-09-21
Hi,

I would recommend you to install the "Ubuntu Restricted extras" package from the Software repository. Most of the windows compatible fonts along with some of the codecs are also included in it.

---

### Post by uzumakifahim on 2012-09-21
Thanks for your reply, but I'm not looking for any windows compatible fonts. I need some specific fonts to be installed.

Moreover, there is some development on this issue. I've just found that, the fonts are installed now. I found them on font list of gedit. The problem is that they are absent in the font list of LibreOffice. So, the problem is may be LibreOffice related.

---

### Post by grahammechanical on 2012-09-21
Set the file manager View menu to show hidden files and look in your home folder for a folder called .fonts

The dot ( . ) in front of the folder name is what makes it a hidden folder. That is where you need to copy those font files that you have.

I have three special fonts that I was using to give Greek and Hebrew characters. And it is the .fonts folder that they are stored. And they do appear in Libreoffice.

If you do not have that folder then create it and copy the files there.

Regards.

---

### Post by uzumakifahim on 2012-09-21
> **grahammechanical said:**
> Set the file manager View menu to show hidden files and look in your home folder for a folder called .fonts

The dot ( . ) in front of the folder name is what makes it a hidden folder. That is where you need to copy those font files that you have.

I have three special fonts that I was using to give Greek and Hebrew characters. And it is the .fonts folder that they are stored. And they do appear in Libreoffice.

If you do not have that folder then create it and copy the files there.

Regards.

IT WORKED!!! Really many many thanks for the solution,but in past I've used the method (first post in this thread) and that worked great. Why this time it's different? Could you please clarify?

Regards.

---

