---
title: "Embedding files in a bash script?"
date: 2012-10-09
forum: General Help
---

### Post by Stonecold1995 on 2012-10-09
How do I embed a data file (e.g. audio, video, compressed, etc) in a bash script, so that the bash script can extract/create a file from itself?  Would something like this work?

```
#!/bin/bash

cat << _AUDIO > /tmp/music.mp3
[B]contents
of
audio
file[/B]
_AUDIO

mpg123 /tmp/music.mp3
rm /tmp/music.mp3
exit 0
```

Or how else can this be done?  I know the TrueCrypt installer does this, so I know it can be done.

---

### Post by spjackson on 2012-10-09
I am pretty sure that I have seen installer scripts which contain binary data, but I would be concerned about:
a) risk of corruption by my text editor
b) the unwanted but necessary newline at the end of file

There may be a workaround, e.g. if you embed a tar archive, but I'm not sure. Personally I'd opt for encoding the data. This makes your install script slightly larger, which may or may not be significant.

```

base64 < music.mp3 > temp.tmp

```
Load temp.tmp into your script, then: 

> **Stonecold1995 said:**
> 
```
#!/bin/bash

base64 -d << _AUDIO > /tmp/music.mp3
contents
of
temp.tmp
_AUDIO

mpg123 /tmp/music.mp3
rm /tmp/music.mp3
exit 0
```



You'd need to check whether base64 is installed by default, or at least whether you could rely on it being on all intended targets. There are alternative encoding/decoding mechanisms.

It might be worth looking at some scripts that do this.

---

### Post by Stonecold1995 on 2012-10-09
Thank you, it worked.

Are there other encoding methods that encode/decode quicker or provide smaller file sizes?

---

### Post by spjackson on 2012-10-09
No, I don't know of anything better. uuencode is older and no better than base64.

---

### Post by Merrattic on 2012-10-09
This is very clever, but I am struggling to find a useful application for this...?

---

