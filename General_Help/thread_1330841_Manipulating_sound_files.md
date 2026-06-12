---
title: "Manipulating sound files"
date: 2009-11-18
forum: General Help
---

### Post by macroshaft on 2009-11-18
I have roughly 2500 zip files containing an .mp3 and a .cdg file in each. For each of these I need to extract the mp3 and then create a preview of the mp3, say the first 20 seconds. Does anyone know a command that would automate doing this?

Any solution would greatly speed up my work.

The files came to me named but I needed them numbered so using help off here I've already listed them to a file

ls ./*.mp3 >> filelist.txt

taken those seperate files and merged them into the zips

ls *.mp3 | sed "s/\.mp3$//" | while read file; do zip -j "$file" "$file".mp3 

and then numbered those zips accordingly

i=0; for f in *; do mv "$f" ./$(printf %04d $i).zip; ((i++)); done

so I'm sure there will be a command to do something this repetative.

---

### Post by macroshaft on 2009-11-18
I have downloaded cutmp3, it looks like I should be able to arrange the commands I already have to create a counting loop which will unzip each file in turn, edit the mp3 and then save it into a file numbered the same as the zip.

---

