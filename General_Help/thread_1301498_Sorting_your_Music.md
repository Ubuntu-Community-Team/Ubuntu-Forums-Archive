---
title: "Sorting your Music"
date: 2009-10-26
forum: General Help
---

### Post by 7raTEYdCql on 2009-10-26
Sometimes when i add songs to my Rhythymbox, the player doesn't recognize the artists and/or Song names. It then becomes a problem for me to identify my songs, with rhythymbox.

Is there a way, to change the Audio Tags for all songs within a directory structure, to a particular Artist. Cause going to individual songs and changing, is kinda cumbersome.

Is there any software which can help me doing this?

---

### Post by nothingspecial on 2009-10-26
easytag will let you do that

---

### Post by 7raTEYdCql on 2009-10-26
Thanks for that, i went through the documentation pages and the conversion specifier for cd no doesn't exist. Now if i want to change the cd no for a whole album, how can this be done, apart from the manual old fashioned way?

---

### Post by x C0MMAND0 x on 2009-10-27
If you import using Audio CD Extractor (sound-juicer) into your /home/user/music folder, it usually recognizes all of the CDs for you.  Then, just do a rescan on your collection (usually only takes a few seconds) and the new tracks will be added.

I have never liked ANY audio-applications CD-ripper and prefer to use a program designed specifically for it.

---

### Post by mobilediesel on 2009-10-27
I use MusicBrainz Picard
```
sudo apt-get install picard
```

[quote=musicbrainz.org]Picard is the next generation MusicBrainz tagging application. This new tagging concept is album oriented, as opposed to track/file oriented like the ClassicTagger was. Picard is written in Python, which is a cross-platform language, and makes use of cross-platform libraries - this allows the same code to run both on Windows, Linux and Mac OS X.[/quote]

It can sort music files into directories by artist, album, disc number in whatever order you want. If it can't find the name of a track it can also scan the fingerprint of the file to get the proper tags for it.

---

