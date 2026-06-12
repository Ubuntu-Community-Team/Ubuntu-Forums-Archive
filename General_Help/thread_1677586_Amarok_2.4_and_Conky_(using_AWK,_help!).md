---
title: "Amarok 2.4 and Conky (using AWK, help!)"
date: 2011-01-28
forum: General Help
---

### Post by chowanec on 2011-01-28
Hey all -- this was working under 2.3, but it looks like they threw in AlbumArtist as part of the GetMetaData command in 2.4 :P.

Here's all the metadata for a particular track:
```

album: Summer of Fear
albumartist: Miles Benjamin Anthony Robinson
artist: Miles Benjamin Anthony Robinson
arturl: amarok-sqltrackuid://1480f28de21b8b2a87f4463bc7a2dc16
audio-bitrate: 261
audio-samplerate: 44100
comment: Amazon.com Song ID: 212954979
genre: Indie
location: file:///home/chow/Network/Music/Miles%20Benjamin%20Anthony%20Robinson/Summer%20of%20Fear/02%20-%20Always%20an%20Anchor.mp3
lyrics: "www.lyricsplugin.com"

Upgrade to Lyrics Plugin version 0.4
mtime: 252000
rating: 0
time: 252
title: Always an Anchor
tracknumber: 2
year: 2009

```

And my problem is this -- when I awk for the artist: line, I get both the Artist and the AlbumArtist metadata lines.  Is there a way to isolate JUST "artist:" and have it ignore/skip "albumartist:"?

Command:
```

qdbus org.kde.amarok /Player GetMetadata | awk '/artist:/{print substr($0,9)}' | tr '[A-Z]' '[a-z]'

```

Output:
```

ist: miles benjamin anthony robinson
miles benjamin anthony robinson

```

The first line, as you can see is from the albumartist: entry and the second (correct) line is for the artist: entry.  Obviously this is screwing up my once-beautiful conky setup. :P

I stole this script from someone ages ago -- and I don't quite understand the intracacies of awk yet. :P

Help?

-Chow

---

### Post by DaithiF on 2011-01-31
Hi,
change the awk pattern to /**^**artist:/
(the ^ anchors the pattern to the start of a line).

---

