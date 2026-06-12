---
title: "MP3 player loses tags"
date: 2011-08-29
forum: General Help
---

### Post by steviefordi on 2011-08-29
I have tried copying MP3 files to my media player using Rhythmbox. Although the Album/Artist/Name tags are present, the device doesn't recognise them. 

When using the device everything goes into the "Unknown Album" and "Unknown Artist" sections.

The device is a "Creative Zen Mozaic EZ300"...

Any ideas?

---

### Post by AlphaLexman on 2011-08-29
There are two completely different and unrelated methods to store the metadata inside an mp3. You probably are using one, while your player expects the other. See [http://en.wikipedia.org/wiki/ID3]("http://en.wikipedia.org/wiki/ID3"). 

**NOTE:** It is perfectly acceptable to have both ID3 containers in your mp3(s).

---

### Post by kartabosh on 2011-08-29
> **steviefordi said:**
> I have tried copying MP3 files to my media player using Rhythmbox. Although the Album/Artist/Name tags are present, the device doesn't recognise them. 

When using the device everything goes into the "Unknown Album" and "Unknown Artist" sections.

The device is a "Creative Zen Mozaic EZ300"...

Any ideas?

here's a guide i wrote a while back while experiencing difficulties with tags on my sony walkman

[http://crunchbanglinux.org/wiki/howto/mp3_tagging](http://crunchbanglinux.org/wiki/howto/mp3_tagging)

---

### Post by steviefordi on 2011-08-30
Thanks for the advice. I have a plan which is as follows...

[LIST]
[*]Get onto a Windows PC and install the software that is supplied with the device.
[*]Put some tracks onto the device using the software.
[*]Examine the tags to ascertain the ID3 version. 
[/LIST]

Hopefully I can then emulate what the supplied software does when pushing tracks to the player.

---

### Post by steviefordi on 2011-09-01
It seems the player expects ID3v2.3 tags and Rhythmbox (via gstreamer) is producing ID3v2.4.

Two options to fix
[LIST]
[*]install the gstreamer-bad-plugins and amend the gstreamer pipeline for MP3 ripping in Rythmbox to use id3mux instead of id3v2mux (not sure if this will work).
[*]Use a tag editor (such as EasyTag) after ripping to amend the tags to a readable version (works like a charm! ;)).
[/LIST]

---

