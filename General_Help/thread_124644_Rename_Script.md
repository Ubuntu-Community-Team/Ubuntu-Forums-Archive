---
title: "Rename Script"
date: 2006-02-01
forum: General Help
---

### Post by qalimas on 2006-02-01
I have recently bought a cd/mp3 player that plays burnt mp3 cds.  Now, it needs them in a special format, for example:

album001
-001.mp3
-002.mp3
-003.mp3
album002
-001.mp3
-002.mp3
-003.mp3

What I'm looking for is something that can take the files in a directory (a dir with about 15 mp3 files), and rename them to 001.mp3, 002.mp3, so on and so forth.  It would need to do it in order, for example, if the file names are 01_craig-david_fille-me-in.mp3, 02_craig-david_song2.mp3, it could rename them in order to 001.mp3 and so on to keep the album in order.  It's awefulto copy and rename all these files by hand xD

I'm sorry if that's a littel confusing, I got confused a couple of times writting it, but any help is appreciated :D

---

### Post by kabus on 2006-02-02
I think this should work as long as the files are already in the right order.
No guarantee that this is the best way, that it will work in all cases or that it won't do something horrible to your files, so better test it first. :) 

```
#!/bin/bash
n=0
pad="00"
ext=".mp3"
for i in *.{mp3,MP3}; do
  n=$(( $n +1 ))
  [ $n -eq 10 -o $n -eq 100 ] && pad=${pad:$(( ${#n} -1))}
  mv "$i" "$pad$n$ext"
done
```

---

