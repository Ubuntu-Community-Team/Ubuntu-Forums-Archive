---
title: "How can I list all files recursively with absolute paths?"
date: 2012-06-30
forum: General Help
---

### Post by Maheriano on 2012-06-30
I got one directory and I want to list all the files from that directory recursively. I only want to list the .mp3 and .flac files and I want to display the full path location to that file along with the file name. Is there a way to do this from the terminal? Thanks.

---

### Post by VCoolio on 2012-06-30
with bash >= 4.0 and globstar enabled (shopt -s globstar), you could do:

for i in **/*.{flac,mp3}; do echo $(pwd)/$i; done

meaning: for each file ending with .flac or .mp3 found recursively from the current folder, print path_to_there/filename.

---

### Post by steeldriver on 2012-06-30
... or I think you could just use 'find'

```
find . \( -name '*.mp3' -o -name '*.flac' \) -print
```

---

