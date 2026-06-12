---
title: "List extensions in a directory"
date: 2011-03-14
forum: General Help
---

### Post by rnelson0 on 2011-03-14
Okay all you command line wizards. I'm trying to clean up and sanitize my music directory. I first want to start off by finding all the file types/extensions that I have in my music folder. This folder contains MP3 files (duh), some JPG files, some INI files, etc. I first want to get a list of all the extensions under my music directory.
Something like this:

```

$ {some command or script} /home/FRED/Music/
.mp3
.jpg
.ini
.ogg
.m3u

```

Using that I would then just delete all the file types that aren't audio files... but first I want to know what I have in there.

Anyone have any tricks to get that kind of output?

---

### Post by sisco311 on 2011-03-14
Try something like:
```
for file in /home/FRED/Music/*.* ; do
  echo "${file##*.}"
done | sort | uniqe
```

---

### Post by rnelson0 on 2011-03-14
That script works almost perfectly! I should have mentioned that I needed it to search recursively under the Music directory. If I modify /home/FRED/Music/*.* to /home/FRED/Music/*/*.* I can go deeper into the directories. This is not ideal, but its a workaround.

---

### Post by sisco311 on 2011-03-14
In bash 4 you can use globstar:
```
shopt -s globstar
for file in /home/FRED/Music/**/*.*; do 
  echo ${file##*.}
done | sort | uniq
```

See:
```
man bash | less +/"^ +Pattern Matching"
```

---

