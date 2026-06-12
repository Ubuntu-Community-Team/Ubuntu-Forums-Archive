---
title: "Joining MP3 files losslessly"
date: 2010-10-24
forum: General Help
---

### Post by oshirowanen on 2010-10-24
I have a bunch of MP3 files and I have their paths grouped in a text file. Is it possible to join the relevant MP3 files based on the paths in the text file losslessly?

---

### Post by cannywizard on 2010-10-24
Try this 
[http://ubuntuforums.org/showthread.php?t=193144](http://ubuntuforums.org/showthread.php?t=193144)

---

### Post by amauk on 2010-10-24
Can I suggest if you use cat, then also rewrite the MP3 frame headers
Else seeking will not work, and some players may even refuse to play it because of mismatching header info

```
ffmpeg -i catted_mp3 new_mp3
```

---

