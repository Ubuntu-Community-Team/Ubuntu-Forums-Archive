---
title: "Music converter from WMA to, OGG or MP3?"
date: 2005-02-13
forum: General Help
---

### Post by Lynx on 2005-02-13
Is there a usable music converter that will convert WMA to OGG or MP3 or both?

---

### Post by evangelion on 2005-02-13
You can use mplayer to dump the file to wave
```

mplayer -ao pcm some.wma

```

It will create a file called audiodump.wav which you can feed to lame to create an mp3 out of, or oggenc to create an ogg out of

```

lame -b [bitrate] audiodumb.wav newmp3.mp3
oggenc -b [bitrate] audiodump.wav

```

It's easy enough even if it's not terribly convenient, if you had a lot of them to do you could make a bash script I suppose.

I'm sure there's a better way, but this is the only way I know of.

---

### Post by fdoving on 2005-03-15
[QUOTE=Lynx]Is there a usable music converter that will convert WMA to OGG or MP3 or both?[/QUOTE]
 Guide to converting: [http://www.linuxquestions.org/questions/answers/352](http://www.linuxquestions.org/questions/answers/352)

---

