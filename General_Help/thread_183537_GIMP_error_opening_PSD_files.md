---
title: "GIMP: error opening PSD files"
date: 2006-05-28
forum: General Help
---

### Post by megamania on 2006-05-28
I have quite a few pictures (around 1000) which I saved in PSD format some time ago. They are scans from negatives, so there are no layers or things like that.
Very few of them (I think the black and white ones) can be opened in gimp, but most of them can not. This is the message I get:

> Opening /home/xxx/aaa.psd failed: Plug-in could not open image

I read that this problem usually happens when the images are saved using the  CMYK color set. I'm pretty sure (although not 100%) that I used either Adobe RGB or sRGB.

I don't have Windows anymore, and I don't want to reinstall it. What can I do to (a) open the images with linux (I would save them in TIF afterwards) or (b) check if I actually saved them in CMYK?

Please give me your advice - I didn't think I would have missed Windows again...

---

### Post by Randomskk on 2006-05-28
If the problem is indeed CMYK, consider using Krita. It's a less powerful image editor, for the KDE suite, but it can do CMYK and as far as I can see it can open .psd.

Sudo apt-get install krita
should work, although it will pull in a few other files while it's doing it (just those needed for krita to run).

If you like, send me a .psd that GIMP won't open and I can see if Krita will open it, to save you from installing if it doesn't work.

---

### Post by megamania on 2006-05-28
[QUOTE=Randomskk]If the problem is indeed CMYK, consider using Krita. It's a less powerful image editor, for the KDE suite, but it can do CMYK and as far as I can see it can open .psd.[/QUOTE]
It will work under Gnome, right? I'm using Ubuntu Dapper

[QUOTE=Randomskk]If you like, send me a .psd that GIMP won't open and I can see if Krita will open it, to save you from installing if it doesn't work.[/QUOTE]
The images are >30Mb each, so it could be a problem sending them by email, but thanks for offering!

I'll try Krita and will let you know.

---

### Post by Randomskk on 2006-05-28
Yup, it will work fine under GNOME, although some KDE libs will get installed. Not KDE itself, though.

---

