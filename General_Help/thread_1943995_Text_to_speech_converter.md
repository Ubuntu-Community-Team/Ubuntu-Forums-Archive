---
title: "Text to speech converter"
date: 2012-03-20
forum: General Help
---

### Post by Mashe on 2012-03-20
hey, i want to convert my text file into speech,and store that audio file for future use.
how can i do this task?(i m using python)
pls rep.

---

### Post by stinkeye on 2012-03-20
If festival is installed, you can use
```
text2wave myfile.txt -otype snd -o myfile.wav
```

---

