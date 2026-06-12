---
title: "Fonts problem in LibreOffice"
date: 2011-07-24
forum: General Help
---

### Post by Desd on 2011-07-24
Hi all,

I have a weird problem with 2 fonts I installed manually. I downloaded both files and installed them via Nautilus (double-click opens installer window, click install => all looked fine). I can use the fonts with GIMP, but neither LibreOffice, nor Fontmatrix finds the fonts.

So, I also installed them via the terminal in the /usr/share/fonts/truetype/ folder and cleared the cache:
```
sudo cp ~/Downloads/ITC /usr/share/fonts/truetype/
sudo fc-cache -f -v
```
This was the output of cache clearing:
```
/usr/share/fonts: caching, new cache contents: 1 fonts, 4 dirs
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
/usr/share/fonts/truetype: caching, new cache contents: 3 fonts, 21 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: caching, new cache contents: 60 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/takao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/thai: caching, new cache contents: 54 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 21 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-droid: caching, new cache contents: 9 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: caching, new cache contents: 17 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-kacst-one: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-khmeros-core: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-liberation: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-linex: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-punjabi-fonts: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-rufscript: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-sil-galatia: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-symbol-replacement: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/truetype/ttf-symbol-replacement/symbol-replacement.ttf: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ubuntu-font-family: caching, new cache contents: 6 fonts, 0 dirs
/usr/share/fonts/truetype/umefont: caching, new cache contents: 18 fonts, 0 dirs
/usr/share/fonts/truetype/unfonts: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/wqy: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 2 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/fonts/type1/mathml: caching, new cache contents: 1 fonts, 0 dirs
/usr/X11R6/lib/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/[USER]/.fonts: caching, new cache contents: 2 fonts, 0 dirs
/home/[USER]/.Fontmatrix/Activated: caching, new cache contents: 0 fonts, 0 dirs
/var/cache/fontconfig: cleaning cache directory
/home/[USER]/.fontconfig: cleaning cache directory

```

Nothing changes after this second install / clearing and reboot. I am still able to use the fonts in GIMP, but not in LibreOffice / Fontmatrix. I am lost, how can I use the fonts in LibreOffice? Using Ubuntu 11.04.
Thanks in advance!
Greetings,

---

### Post by bapoumba on 2011-07-24
You may need to log out and log back in.

Edit : [http://listarchives.libreoffice.org/global/users/msg01354.html](http://listarchives.libreoffice.org/global/users/msg01354.html)

---

### Post by Desd on 2011-07-24
Thanks bapoumba, 

Did not mention that, but I have been doing that after each step... still no luck. I also found the post you link too earlier on.

Any other ideas? I find it strange that GIMP finds them (even without reboot), but LibreOffice doesn't. Pulling my hair out, for I'd like to finish up my project.

Thanks for any help!

---

### Post by Irony on 2011-07-24
I put fonts in my home folder;

```
~/.fonts
```

they show up in Libreoffice.

---

### Post by Desd on 2011-07-24
Hi Irony,

That is where the fonts end up when you install them via the fontsintaller. Tried copying them there too, but with no luck so far...

Any other ideas?
Thanks!
Greetings,

---

### Post by bapoumba on 2011-07-24
Best offer I can make is to give a link to the fonts and we'll try out :)

---

### Post by Desd on 2011-07-24
see pm for a link.
Greetings,

---

### Post by bapoumba on 2011-07-24
Okay, got them. Same behavior as your for now (ie OK in GIMP but not in Libreoffice), I'll look around.

Installed them with font viewer.
Edit: they are in ~/.fonts

---

### Post by bapoumba on 2011-07-24
Hmm, not working in gedit either. Did not find anything interesting around. At first I though it was the Libreoffice version Ubuntu ships that had problems, but now I think the fonts files themselves have problems :)

---

### Post by Desd on 2011-07-24
Thanks for the effort! Waiting patiently for any insights... :popcorn:
Greetings,

---

### Post by bapoumba on 2011-07-24
[http://openoffice.org/bugzilla/show_bug.cgi?id=16032](http://openoffice.org/bugzilla/show_bug.cgi?id=16032)

This bug is for Openoffice, but I guess it still applies to Libreoffice. This is what I am trying to find out.

---

### Post by Desd on 2011-07-24
Thanks, I would not have found that bug-report. However I do not fully understand the issue discussed there. It seems to apply to .otf files, while I tried to install .ttf files. Or am I missing something?
Greetings,

---

### Post by bapoumba on 2011-07-25
May be I am the one missing something :)
It was late for me yesterday when I found the report. I'll read that over and maybe in the mean time someone else will chime in. I'll try to get in touch with Hagar who knows much about office suites.

---

### Post by Hagar Delest on 2011-07-25
Bapoumba sent me the font files and no problem with Gedit, LibO (3.4.1) and OOo (3.3.0) on Natty. I just extracted them in my ./fonts folder and launched OOo, LibO and Gedit, they see them right away. NB : These fonts were not installed previously of course.

NB: I use only the vanilla version for each (instead Gedit delivered with Ubuntu of course): [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by Desd on 2011-07-26
Thanks Hagar. I see you use LO 3.4.1-native, where I use LO 3.3.2-ubuntu... Could that be the problem. I will update to your version and see if that works. Thanks for looking into it.
Greetings,

---

### Post by Hagar Delest on 2011-07-26
Since it works fine with OOo 3.3.0, I think that it should work also with LibO 3.3.x. The higher the LibO version is, the more different is the code.

---

### Post by Desd on 2011-07-26
See the logic there... But then, how come that both bapoumba and I have problems with using them in LO? Or better (since I don't really care for the answer), how can we start using the fonts? Any ideas on how to correct this behaviour?
Thanks!
Greetings,

Jeroen

---

### Post by Hagar Delest on 2011-07-26
The main difference seems to be that I use the vanilla versions, not the versions provided by Ubuntu.

---

### Post by Desd on 2011-07-27
Well, that would explain it too. Thanks for your effort, but unfortunatly, my deadline for my project and my aesthetic ambitions can not co-exist. I will for now stop trying to get this font in my project, hand over the result and enjoy my holiday. If I get it back to work as it should, I'll report here.
Thanks again!
Greetings,

---

### Post by Hagar Delest on 2011-07-27
Anyway, it is said that it's better to avoid sans serif fonts for printed material. Sans serif looks better on screen but are less readable when printing on paper (I rather agree).

If you want some very good fonts with ligatures and plenty of aesthetic effects, look at Linux Libertine: [Automatic ligature support through graphite fonts](http://user.services.openoffice.org/en/forum/viewtopic.php?f=49&t=32910).

---

### Post by EdgardL on 2011-08-20
> **Desd said:**
> Well, that would explain it too. Thanks for your effort, but unfortunatly, my deadline for my project and my aesthetic ambitions can not co-exist. I will for now stop trying to get this font in my project, hand over the result and enjoy my holiday. If I get it back to work as it should, I'll report here.
Thanks again!
Greetings,

Dear Desd (, Hagar, bapoumba)

I don't know whether the present message will be useful, but I managed to solve a similar problem I encountered three weeks ago. I searched and found an OpenType font file and installed it, using the Font Viewer via Nautilus. Similar behaviour as described by you: the font was visible under The Gimp but not under LibreOffice. However, the font file name lacked the extention ".otf" (a detail I neglected until today). Today, I de-installed the font, changed the file name by appending ".otf" to it and repeated the installation procedure, and this time LibreOffice also notices the presence of the font. Note: I run Ubuntu 11.04 and have LO 3.3.3-1ubuntu2 at this moment.

---

### Post by jeff_finger on 2012-07-06
In Ubuntu 12.04 I did the following:

1. Renamed the Type1 files such that the suffix became lower case, that is, .afm and .pfb rather than .AFM and .PFB.

2. Put the files under /usr/share/fonts/, in my case two levels beneath /usr/share/fonts.

3. Made sure the files were readable

4. Ran "sudo fc-cache -f -v"

Then, I shut down OpenOffice, started it again, and everything worked fine. The Type1 fonts were also visible is LibreOffice.

---

### Post by wildmanne39 on 2012-07-06
Hi, this is an old thread so it has been closed, thanks for sharing.

---

