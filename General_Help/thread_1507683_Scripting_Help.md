---
title: "Scripting Help"
date: 2010-06-11
forum: General Help
---

### Post by gingivere0 on 2010-06-11
I would like to make a script for converting music using ffmpeg.  I have a lot of music that I would like to convert to a different format and I don't want to have to do it manually each time. At the moment, I am using this command to convert the music:

```
ffmpeg -i <nameofsong>.* <nameofsong>.mp3
```

Any and all replies are appreciated! Thanks!

---

### Post by Zeosa on 2010-06-11
> **gingivere0 said:**
> I would like to make a script for converting music using ffmpeg.  I have a lot of music that I would like to convert to a different format and I don't want to have to do it manually each time. At the moment, I am using this command to convert the music:

```
ffmpeg -i <nameofsong>.* <nameofsong>.mp3
```

Any and all replies are appreciated! Thanks!


It's not guaranteed to work, or refined, but it should do the job...
```


#!/bin/bash

for filename in `ls ./`
do

ffmpeg -i $filename $filename.mp3

```

Again, just a quick/dirty script which is worth exactly what you paid for it :) ....should attempt to convert all files in the current directory to mp3. ..it's at least a starting point for your research.

---

### Post by kevin.krenz on 2010-06-11
I would recommend using the Sound Converter software available in the Software Center - you can choose directories, plus you can customize the naming of the files, specify whether the original files are deleted, etc.

---

### Post by gingivere0 on 2010-06-11
Sorry I'm extremely new to scripting (this being my first time),  what do i do with that code?

---

### Post by gingivere0 on 2010-06-11
nvm, I figured it out. But unfortunately, whenever I run the script it says "line 7: syntax error: unexpected end of file"

---

### Post by Zeosa on 2010-06-12
Sorry, twas just before bedtime last night when I posted that, stick 'done' at the end of the script like this...


```

#!/bin/bash

for filename in `ls ./` ; do

ffmpeg -i $filename $filename.mp3

done

```

---

### Post by gingivere0 on 2010-06-12
Thanks! It works perfectly!

---

