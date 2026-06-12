---
title: "Moving with a set wildcard/variable?"
date: 2010-05-16
forum: General Help
---

### Post by ownaginatious on 2010-05-16
I would like to move a bunch of files and rename them at the same time, but I'm having trouble figuring out how to do this.

Here is what I would like to do:

```
mv Something-[A].mp3 [A]-Something.mp3
```

Where [A] would represent the string found after "Something-" in an MP3s file name.

Is there something built in that does this?

Thanks!

---

### Post by sisco311 on 2010-05-17
GUI tools:
[list]
[*]thunar (file manager)
[*]gprename (gtk)
[*]purrr (gtk)
[*]pyrenamer (gtk)
[*]gwenrename (qt)
[*]krename (qt)[/list]

CLI:

prel based rename command:
```
rename -n 's/Something-(.*).mp3/$1-Something.mp3/' *.mp3
```
remove the -n option to actually rename the files.

or try something like:
```
for file in *.mp3; do newfile="${file//Something-/}"; newfile="${newfile//.mp3/}"; **echo** mv -b "${file}" "${newfile}-Something.mp3"; done
```
remove the echo command to actually rename the files.

---

