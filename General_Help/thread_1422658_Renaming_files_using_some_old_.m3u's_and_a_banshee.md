---
title: "Renaming files using some old .m3u's and a banshee .db"
date: 2010-03-05
forum: General Help
---

### Post by bob_hilton on 2010-03-05
In a recent accident i've wiped 3-4 years of fanatical order and all tags from my 4075 audio files.

I have a banshee.db backup and a couple of old .m3u's that i can recover the info from but just need some help using it. 

I know i can use regular expressions to pin-point the stuff i need but i dont know how to put it into practice?! 

Any help would be appreciated!


To give an idea this is what i have/need

I have most of the files named like this:

/home/andrew/Music/Artists/Foals/Antidotes/Antidotes - 11 - Foals - Tron.mp3

but some with information missing from the filename or slight differences in naming- e.g.

/home/andrew/Music/Artists/Foals/Antidotes/11.Tron.mp3

I know that i can locate the files as the paths havn't changed and all of my files end in the track title followed by the filetype. 

What i want to do is add extra info like the rating and genre of all of these to the filenames so that i can then use ex-falso or fb2k to re-populate the tags.

---

### Post by Intrepid Ibex on 2010-03-05
[http://ubuntuforums.org/showthread.php?t=293087](http://ubuntuforums.org/showthread.php?t=293087).

We call this searching with the search feature.

---

### Post by bob_hilton on 2010-03-05
i didnt explain myself properly..

my filenames store the album and title but thats about it. the data in banshee.db stores path, album ,artist, title, rating & genre like this:

/home/andrew/Music/Artists/Foals/Antidotes/[COLOR="Red"]Antidotes - 11 - Foals [/COLOR]- Tron.mp3|3|Alternative|Tron|Foals|Antidotes
/home/andrew/Music/Artists/Elbow/The Seldom Seen Kid/[COLOR="Red"]01 - Mirrorball.flac[/COLOR]|5|Alternative|Mirrorball|Elbow|The Seldom Seen Kid
/home/andrew/Music/Compilations/Cocoon - Sexy Techno/[COLOR="Red"]Cocoon - Sexy Techno - 07 - Isotope.mp3[/COLOR]|4|Techno|Isotope|Isotope|Cocoon - Sexy Techno

one line for each file in the db. My file system looks a little different to the entrys in the .db as i've renamed some files since using banshee. The section in red varies but all end in *" - tracktitle.ext "*

I need to rename the files using the info from each line in the .db that corresponds with the actual files but don't know which commands to use from th terminal to strip the data i have an append it to the file name.

---

