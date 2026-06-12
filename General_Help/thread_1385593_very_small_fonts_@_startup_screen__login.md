---
title: "very small fonts @ startup screen / login"
date: 2010-01-19
forum: General Help
---

### Post by Bloemetjesgordijn on 2010-01-19
Hi,
For some time now (actually, since I migrated to KUbuntu) the fonts at "log in" / "start up" are way to small to read.

After start up / log in every thing is normal.
Normal or proprietary drives makes no difference


Current setup:
Kubuntu 9.10 64 bits
Ati Video card
Monitor: Sony LCD screen (a TV)

help is appreciated :-D

Kind regards,

Bloemetjesgordijn

---

### Post by Zorael on 2010-01-20
When X (the graphical environment) starts, it tries to autodetect your screen dimensions and figure out what dpi setting (dots per inch) to use for fonts. The de facto standard is 96, but someone somewhere thought it'd be nice if fonts were the same physical size on all screens everywhere, instead of being the same pixel size everywhere. Sometimes this dpi lookup doesn't really work out and you get insanely huge/tiny fonts.

What you can do is to tell kdm (the login manager) to start X with an argument telling it to specifically use a dpi of 96, or other sane value of choice.

Open up **/etc/kde4/kdm/kdmrc** in a text editor with superuser permissions, such as by running '**kdesudo kate /etc/kde4/kdm/kdmrc**' from a run box (Alt+F2) or a terminal. Find the section that has this line and add the bit in bold green.
```
ServerArgsLocal=-br -nolisten tcp **[COLOR="Green"]-dpi 96[/COLOR]**
```
Just make a text search for 'ServerArgsLocal'.

---

### Post by Bloemetjesgordijn on 2010-01-27
Thx Zorael

for your explanation. I will give it a go and see if it works.

Thx again

Kind regards

Bloemetjesgordijn

---

### Post by Bloemetjesgordijn on 2010-01-27
Thx it worked like a charm

---

### Post by barnskybeat on 2010-12-12
How would that work in an Ubuntu 10.10 environment?

---

### Post by Zorael on 2010-12-12
For Ubuntu and other spins using GDM, I think you can add that **[COLOR="Green"]-dpi 96[/COLOR]** argument to **/etc/X11/xinit/xserverrc** instead.

```
#!/bin/sh

exec /usr/bin/X -nolisten tcp **[COLOR="Green"]-dpi 96[/COLOR]** "$@"
```
I haven't tried it myself so it may not work, though. From what I can tell GDM seems to have moved away from using a conventional gdm.conf file.

---

### Post by vidtek on 2011-01-30
My thanks to  Zorael as well,

small thing but it's bugged me for ages.

Tony

---

### Post by thomi_ch on 2011-11-20
> **Zorael said:**
> When X (the graphical environment) starts, it tries to autodetect your screen dimensions and figure out what dpi setting (dots per inch) to use for fonts. The de facto standard is 96, but someone somewhere thought it'd be nice if fonts were the same physical size on all screens everywhere, instead of being the same pixel size everywhere. Sometimes this dpi lookup doesn't really work out and you get insanely huge/tiny fonts.

What you can do is to tell kdm (the login manager) to start X with an argument telling it to specifically use a dpi of 96, or other sane value of choice.

Open up **/etc/kde4/kdm/kdmrc** in a text editor with superuser permissions, such as by running '**kdesudo kate /etc/kde4/kdm/kdmrc**' from a run box (Alt+F2) or a terminal. Find the section that has this line and add the bit in bold green.
```
ServerArgsLocal=-br -nolisten tcp **[COLOR="Green"]-dpi 96[/COLOR]**
```
Just make a text search for 'ServerArgsLocal'.


hey

exact above was the solution for the problem with small font size in google-earth... strange....

thanks a lot

reagards
thomi

---

### Post by Anatona on 2013-01-25
Thx for the help!

:guitar:

---

