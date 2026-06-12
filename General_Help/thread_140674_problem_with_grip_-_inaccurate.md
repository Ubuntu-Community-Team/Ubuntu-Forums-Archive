---
title: "problem with grip - inaccurate"
date: 2006-03-06
forum: General Help
---

### Post by foxy123 on 2006-03-06
I decided to rip my cds to the hd. I tried sound juicer but it is not very configurable. Grip is very good as it allows me to configure things I like. But... there is always a 'but'.

I rip CDs in ogg using encogg. Well, it looks like Grip rips CDs sort of inaccurately. At least freedb does not recognise them, while ripped with sound juicer is recognised ok. Another thing Grip does not insert track Nos..

Does anyone experience something like that?

---

### Post by astoltz on 2006-03-06
Could be they are not recognized because the ID3 tags are not getting written.  Look in the Config tab, then in the ID3 tab.  There is a box that says "Only tag files ending in .mp3" - make sure that's unchecked.

Also, for the track number.  Again in the config tab, this time go to Encode.  There is a line for Encode file format.  There are a bunch of % switches in that line that add parts to the file name (%n for the name of the track for instance).  Put in %t to add the track number to the file name.

---

