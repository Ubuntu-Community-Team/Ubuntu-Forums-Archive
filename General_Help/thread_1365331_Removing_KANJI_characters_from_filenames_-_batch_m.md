---
title: "Removing KANJI characters from filenames - batch mode"
date: 2009-12-27
forum: General Help
---

### Post by TBerk on 2009-12-27
I'd like to find a batch renamer util that supports removing/replacing Japanese characters with English and/or , well- nothing.  

I don't necessarily need a translator as part of the solution, what I want to do is rename files but not change/convert the contents.

I've been trying to find such a thing via search engines, both here in the forum and over the web, as well as via Synaptic- all to no avail.


Thx in advance,
TBerk

---

### Post by Barriehie on 2009-12-27
> **TBerk said:**
> I'd like to find a batch renamer util that supports removing/replacing Japanese characters with English and/or , well- nothing.  

I don't necessarily need a translator as part of the solution, what I want to do is rename files but not change/convert the contents.

I've been trying to find such a thing via search engines, both here in the forum and over the web, as well as via Synaptic- all to no avail.


Thx in advance,
TBerk

I might have a bash script that can do that.  What it does now is rename files with a 10 character random string.  Would take a bit of rewriting because now it's a daemon that monitors a directory.  Are you familiar with bash?  I'm not an expert by any stretch but this works. :)

Barrie

Edit: Okay, I just tried rewriting my script to rename files and *didn't* confine the script to the working directory, it ended up following the ..'s and my home folder was full of random file names! :(  Not bad though because I had done a backup about 2 hours prior.  So, if you're more bash aware than I am... :)

---

### Post by TBerk on 2009-12-27
[QUOTE... it ended up following the ..'s and my home folder was full of random file names! :(  Not bad though because I had done a backup about 2 hours prior.  So, if you're more bash aware than I am... :)[/QUOTE]

Such sacrifice in the quest to help another, my hat is off to you! 

IN the mean time I'm loosing pull down menus in Firefox (and Right Mouse Click as well...) but that is another matter altogether. 

What I was hoping (and scouring the Net last night) was a translation Util, saving that a renamer that I could use to rename (folders mostly).

I gave up doing each one by hand back in the good old DOS days <shudder>.

They can just stay the way they are for now, I wouldn't mind the BASH widget but I'd be still banging up against non-Roman characters in the end.


Thx,
berk

---

### Post by Barriehie on 2009-12-27
Come to think of it Thunar has a bulk rename facility.  Applications > Accessories > Bulk Rename.  Might be the ticket!

Barrie

Edit: Seems this is needed often. [http://ubuntuforums.org/search.php?searchid=68543350](http://ubuntuforums.org/search.php?searchid=68543350)

---

