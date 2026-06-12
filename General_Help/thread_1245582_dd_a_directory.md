---
title: "dd a directory??"
date: 2009-08-20
forum: General Help
---

### Post by AmerNewbieInDE on 2009-08-20
is it possible to dd a dir... or is it only for disks and partitions

---

### Post by andrewc6l on 2009-08-20
Nope, you can't dd a directory. dd works on files only (not just special device files like /dev/hda1) - any file will work.

---

### Post by stinger30au on 2009-08-20
if u want to backup a directory to cd/dvd this litle script will do it for you

[http://sourceforge.net/projects/discspan/](http://sourceforge.net/projects/discspan/)

download the tar file and extract it

in there is a file caled 

discspan.py

copy it to the directory u want to backup

fireup shell and cd to that directory and then type in

python ./discspan.py

follow the prompts

when it asks what drectory u want to backup press the . fullstop key. the fullstop key to shell mans the current directory

enjoy

---

