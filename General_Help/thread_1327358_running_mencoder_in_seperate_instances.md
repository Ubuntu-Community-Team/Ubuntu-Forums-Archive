---
title: "running mencoder in seperate instances"
date: 2009-11-15
forum: General Help
---

### Post by meg23 on 2009-11-15
I am trying to take advantage of a multicore chip by running more than one mencoder instance at time to encode .avi files. My script selects all files in a certain directory and encodes them, however one file at a time. How do I get this script to encode all the files at the same time?

```
mencoder /home/mg/*.avi -oac mp3lame -lameopts cbr:mode=2:br=96 -af resample=44100 -srate 44100 -ofps 20 -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:cbp:trell:vbitrate=1400 -vf scale=720:380 -ffourcc XVID -o recut.avi &
```

---

