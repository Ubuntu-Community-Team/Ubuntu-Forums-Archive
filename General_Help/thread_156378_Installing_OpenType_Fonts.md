---
title: "Installing OpenType Fonts"
date: 2006-04-06
forum: General Help
---

### Post by John Jason Jordan on 2006-04-06
I have several Adobe OpenType Pro fonts. The license allows me to install them on my Ubuntu laptop as well as my Windows desktop. But I can't figure out how to install them on Ubuntu. I want them available for all programs, if possible, but at the very least OpenOffice.org and Scribus. How do I do this?

---

### Post by nanotube on 2006-04-07
have a read of this ubuntu wiki page:
[https://wiki.ubuntu.com/FontInstallHowto](https://wiki.ubuntu.com/FontInstallHowto)

relevant excerpt:
The easiest place to put them [fonts] is
  /home/<username>/.fonts
where <username> is your user name. Any fonts put in this folder well be available to your programs...

that should do it. :)

---

### Post by John Jason Jordan on 2006-04-07
[QUOTE=nanotube]have a read of this ubuntu wiki page:
[https://wiki.ubuntu.com/FontInstallHowto](https://wiki.ubuntu.com/FontInstallHowto)

relevant excerpt:
The easiest place to put them [fonts] is
  /home/<username>/.fonts
where <username> is your user name. Any fonts put in this folder well be available to your programs...

that should do it. :)[/QUOTE]
Thanks for the advice, but it does not work. I did exactly as above, and the fonts are now located in /home/jjj/.fonts, but OpenOffice.org still does not see them. I also put them in /usr/share/fonts, but still nada. I even shut down and restarted the computer.

Note that the fonts I need to install are OPENType, not TRUEType. In fact, they are Type 1s in an OpenType wrapper, not TrueTypes in an OpenType wrapper. They are all Adobe Pro fonts.

I've googled all over about installing OpenType in Linux. I can find lots of sites that say they are "supported," but nowhere can I find anything that says how to install them, except places that tell me the same as your advice. Nowhere do I find anything about what to do when it doesn't work. The Ubuntu Help files do not mention OpenType. (OK, there might be a mention, but the wonderful Ubuntu team forgot to include a search facility in the Help files.)

I'm getting desperate. I have a paper due in a week and I MUST use Adobe Minion Pro for it. If I can't do it on my Linux computer I'll have to borrow a friend's Windows computer. That would suck. 

Anyone else know how to install OpenType Pro fonts on Ubuntu?

---

### Post by nanotube on 2006-04-07
well, i dont know much about fonts... but if these opentype fonts dont work, why not just convert them to truetype, and then use them? i hear a program called "fontforge" can do that for you - and its available in the official repositories. would that work for you?

---

### Post by John Jason Jordan on 2006-04-07
[QUOTE=nanotube]well, i dont know much about fonts... but if these opentype fonts dont work, why not just convert them to truetype, and then use them? i hear a program called "fontforge" can do that for you - and its available in the official repositories. would that work for you?[/QUOTE]
The problem with converting them is that then I lose all the cool features of OpenType -- alternate glyphs, for one thing.

There has to be a way to do it. Lots of sources say you can use OpenType on Linux, so it must be possible.

---

### Post by nanotube on 2006-04-07
just to make sure... when you placed your fonts into /usr/share/fonts, did you update the font db? try the following commands exactly (these are just slightly modified instructions from that wiki page:

```
cd /usr/share/fonts/type1
sudo mkdir opentype
cd opentype
sudo cp /where/your/fonts/are/located/* .
sudo mkfontdir
cd ..
sudo fc-cache 
```

that and then try restarting gnome/rebooting...

---

### Post by John Jason Jordan on 2006-04-07
[QUOTE=nanotube]just to make sure... when you placed your fonts into /usr/share/fonts, did you update the font db? try the following commands exactly (these are just slightly modified instructions from that wiki page:
```
cd /usr/share/fonts/type1
sudo mkdir opentype
cd opentype
sudo cp /where/your/fonts/are/located/* .
sudo mkfontdir
cd ..
sudo fc-cache 
```
that and then try restarting gnome/rebooting...[/QUOTE]
OK, that helped some.

I did exactly the above. All my OpenType fonts are now in /usr/share/fonts/type1/opentype and I did the mkfontdir command. Then I restarted the computer. After Ubuntu was all up and running I launched OO.o Writer with a new, blank document. I typed a few words, selected them, and tried to change the font. None of the OpenType fonts appeared in Writer's font list.

Then I opened Scribus and did the same thing. This time two of the OpenType fonts showed up, but not the rest. Of course, Minion Pro is one of the ones that did not show up. The fonts (family names only) that are now in the /usr/share/fonts/type1/opentype folder are listed below. If it shows up in Scribus I put an asterisk next to it:

Caslon Pro
Garamond Pro
Jenson Pro
Caflish Pro
Calcite Pro
Chaparral Pro
Lithos Pro
Minion Pro
*Myriad Pro
Plantin
Sabon
Silentium
Trajan Pro
*Warnock Pro

When I hover over any of them in my file manager (Konqueror, even though I use Gnome shell), the properties balloon says it is an OpenType font and the font is displayed correctly. So the system seems to be able to handle them.

I thought it might be an OO.o problem (version 1.93.129 on Ubuntu-64 Breezy), but there doesn't seem to be any way in OO.o preferences to tell it where to look for fonts. There is an openoffice folder in /usr/share/fonts, but it has only one font in it, yet many other fonts appear in OO.o menus (just none of the OpenType fonts).

I'm making progress, but it's still not working right.

---

### Post by nanotube on 2006-04-07
well, you might try one other thing
open up nautilus to any folder
then hit <ctrl><l> (that's not number 1, but letter l), that will show you the address bar. in the address bar, type 
```
fonts:///
```
and press enter - it will show you all the fonts that it knows about. see if your "missing" fonts show up.
if not, just drag them in there, and nautilus should install them "automagically". see if that helps. :)

---

### Post by John Jason Jordan on 2006-04-07
[QUOTE=nanotube]well, you might try one other thing
open up nautilus to any folder
then hit <ctrl><l> (that's not number 1, but letter l), that will show you the address bar. in the address bar, type 
```
fonts:///
```
and press enter - it will show you all the fonts that it knows about. see if your "missing" fonts show up.
if not, just drag them in there, and nautilus should install them "automagically". see if that helps. :)[/QUOTE]
OK, more progress!

They are all listed as available to the system.

I also discovered how to get them working in Scribus. You have to tell scribus the folders where the fonts are located. Having done that, now they are all visible in Scribus.

But OO.o still stubbornly refuses to see any of them. So does AbiWord. I can't find a place in either to tell the program where to look for fonts.

---

### Post by nanotube on 2006-04-08
well... i regret to say that i am all out of ideas at this juncture. we are just gonna have to wait for someone more experienced with fonts to come along. :) ...

---

### Post by hopfgartner on 2006-04-14
Have you tried to install fonts for OpenOffice.org with the tool "spadmin" located in  /usr/lib/openoffice2/program/spadmin?

Peter

---

### Post by Breepee on 2006-04-14
OpenOffice has not-so-great OpenType support. I've had OpenType troubbles too in OOo (I could use them, but when exporting to pdf they got 'lost'. It is to be supported sometime in the future, but not yet).

---

### Post by gmcle454 on 2006-05-18
FYI there is a guy working on a font manager for linux that should work like Adobe Type Manager. It is still in early stages of development (VERY EARLY). But something to keep an eye on. Google Linux Font Manager and you should find the freashmeat page.

Good luck to him, for our sakes! Font management and rendering is the only reason I still have to use Windows for graphic design.

---

### Post by AAUBUNTU on 2006-06-04
This is an old thread, but thought I'd reply anyway.  Both AbiWord and OpenOffice have problems with OpenType fonts.  You can find more information by consulting the abiword-user mailing list and the OpenOffice Forums.

[Abiword-user Mailing List Archive]("http://www.abisource.com/mailinglists/abiword-user/") - See Sept 2005 archive

[OpenOffice Forum]("http://www.oooforum.org/") - search for OpenType

---

### Post by Chonnawonga on 2007-03-19
I spent (i.e. wasted) rather a lot of time on this today. In the end I found out that I'd made the simple but stupid mistake of not including ALL parts of the Type1 fonts: the .pfb, .pfm, AND .afm. Oops.

There's more information about using different and difficult font types on OpenOffice [here]("http://www.openoffice.org/FAQs/fontguide.html#5").

Good luck to anyone with this. Font management, like multi-monitor support and a few other things, is still a pain in the @$$ on Ubuntu. (Not that I don't love Ubuntu very dearly.)

---

### Post by rosslaird on 2007-03-28
Though it's not an ideal solution, I have met with success by converting my opentype fonts to truetype (opentype is just a wrapper over truetype anyway).

I used [this link]("http://www.stuermer.ch/blog/convert-otf-to-ttf-font-on-ubuntu.html")

[http://www.se.eecs.uni-kassel.de/~thm/OpenOffice.org/bugs.html](http://www.se.eecs.uni-kassel.de/~thm/OpenOffice.org/bugs.html)

and this script:

```

#!/usr/local/bin/fontforge 
# Quick and dirty hack: converts a font to truetype (.ttf), works only with one font. 
Print("Opening "+$1); 
Open($1); 
Print("Saving "+$1:r+".ttf"); 
Generate($1:r+".ttf"); 
Quit(0);
```

I copied a bunch of otf fonts (Sabon, Kepler, Waters, Stone, etc.) to a test directory, then from within that directory (where the above script -- called otf2ttf.sh was also located) I ran:

```
for font in *.otf ; do fontforge -script otf2ttf.sh $font ; done 
```

Then I was able to install these fonts into OpenOffice using spadmin.

My truetype fonts work perfectly, by the way, in Gnome itself without conversion (I copy them to fonts:///).

Cheers.

Ross

---

### Post by alecwh on 2007-12-22
This thread is old, but it came up in google for me, and the preceding post helped a lot. I'll write how I converted the fonts using the post above a little easier.

Do the following:

```
sudo apt-get install fontforge
```

Now, paste the following into gedit:
```

#!/usr/local/bin/fontforge 
# Quick and dirty hack: converts a font to truetype (.ttf), works only with one font. 
Print("Opening "+$1); 
Open($1); 
Print("Saving "+$1:r+".ttf"); 
Generate($1:r+".ttf"); 
Quit(0);

```

Save the file in your home directory as otf2ttf.sh
Next, execute the following script with the font name replaced in the command:
```

fontforge -script otf2ttf.sh Anivers_31.otf

```

The font should be generated in your home folder. Copy the generated font file into /usr/share/fonts.

Helped me, good luck!

---

### Post by magozoom on 2008-01-20
The .otf files need to be converted to .ttf to work in Open Office 2

I found a hack at 
[http://www.stuermer.ch/blog/convert-otf-to-ttf-font-on-ubuntu.html](http://www.stuermer.ch/blog/convert-otf-to-ttf-font-on-ubuntu.html)

First install fontforge
```

sudo apt-get install fontforge

```

Then create this script and save it as "makettf.sh" in the folder where you have the .otf fonts

```

#!/usr/local/bin/fontforge
# Quick and dirty hack: converts a font to truetype (.ttf)
Print("Opening "+$1);
Open($1);
Print("Saving "+$1:r+".ttf");
Generate($1:r+".ttf");
Quit(0);

```

Then, for each OTF font run
```

fontforge -script makettf.sh FONTNAME.otf

```
and you will get a TTF from your OTF


Maybe a Ubuntu/Linux guru here can give us the correct shell syntax for piping all filenames to the  script - it would be great, something like 

ls *.oft | fontforge -script otf2ttf.sh $1
or similar.... now you have to type them one by one

---

### Post by sylvain.nahas on 2008-01-24
Thanks for the fontforge tip.
it saved my day.

to automate, do

find PATH/TO/FONT/DIR  -name '*otf' -exec fontforge -script PATH/TO/SCRIPT {} \;

for ex:
find /tmp -name '*otf' -exec fontforge -script ~/bin/otf2ttf {} \;

Tchao

---

### Post by Jose Catre-Vandis on 2008-03-11
Thanks this was really handy.

---

