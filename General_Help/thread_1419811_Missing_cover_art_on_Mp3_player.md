---
title: "Missing cover art on Mp3 player?"
date: 2010-03-02
forum: General Help
---

### Post by Nightstrike2009 on 2010-03-02
Hiya everyone,

I have "Banshee" installed and use as an MP3 ripper (& Tag editor) and also use "Easy tag" to add cover art to id3tag data.

The problem I have is Banshee detects all the mp3 id3tag info including the manually added cover art (Added by Easy tag).

However when the music is dragged and dropped to my Sansa Fuze Mp3 player the cover art is not displayed (although it does support it and works with windows equivalents)

Has anyone any ideas on how to fix this?

PS: I am trying to use Ubuntu as main system, I would use Ogg Vorbis but I have heard it doesn't support cover art at all.

---

### Post by Nightstrike2009 on 2010-03-02
The only way I have heard recently is to install Wine and use the windows freeware program;
 "Mp3 Tag v2.45a" from [http://www.mp3tag.de/en/download.html]("http://www.mp3tag.de/en/download.html") 
I didn't really want to resort to using Windows programs but if no-one can come up with an Ubuntu solution guess that's what I am stuck with, oh well its better than no solution at all. :-I

---

### Post by cascade9 on 2010-03-03
I've had no issues with coverart embedded via 'easy tag'. 

Its possible that you are trying to embed art that is too big for your MP3 player. With my iRiver e100 if I try to embed .jepgs bigger than 220x220 (I think, I always make the artwork 200x200) I get no display. Because the e100 supports .png if I embed a .png it works fine no matter the native size (.png resives). I cant be sure with the Fuze but that might be your problem.

BTW,I think that cover art has been added to the .ogg vorbis specifications but it doesn't work with my iriver. Probably the specs havent 'come down the pipeline' to the manufacturers yet.

---

### Post by Nightstrike2009 on 2010-03-04
Thanks for the heads up cascade9,

I have indeed upped the artwork resolution from 128x128 to 200x200 BUT the windows program "Mp3 Tag v2.45a" running under WINE can still add cover art of 200x200 to the Sansa Fuze so I think this maybe the answer:

From Ubuntu Menu Applications>Sound & Video>EasyTAG>

When EasyTAG has loaded up go to Settings>Preferences>ID3 Tag Settings (Tab)

In the "ID3v2 tags" section

Check Write ID3v2 tag option (Probably checked by default)

Change Version to "ID3v2.3" from pull down menu, then click "OK"

PS: EasyTAG is set to ID3v2.4 by default this doesn't seem to make a difference to Ubuntu but does affect certain mobile players (Including Sansa Fuze & Some Sony Models) unless reset to ID3v2.3.

PPS: I haven't had the chance to test this yet but "Mp3 Tag v2.45a" uses ID3v2.3 info, and EasyTAG's default is ID3v2.4. 
The ".4" apparently makes a difference to mobile players (and sometimes seems to write garbage instead of genre in info, also once tagged with ID3v2.4 your only choice is to remove the tag data and re-write them as ID3v2.3 tags).

---

