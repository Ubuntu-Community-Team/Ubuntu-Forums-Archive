---
title: "script to copy files in different folders"
date: 2011-11-02
forum: General Help
---

### Post by publicjo on 2011-11-02
Hi all,

I would like to write a script that would automatically copy files from folders to other folders.

My folders structure is:
~/nifti/ab22311/t1
~/nifti/ab22311/bold
~/nifti/ah01111/t1
~/nifti/ah01111/bold
~/nifti/dd33333/t1
~/nifti/dd33333/bold

ab22311, ah01111, dd3333 being different subjects, and t1, bold being different timepoints
I would like to copy files in this new folder structure:

and I would like to move all the 
~/nifti/t1/ab22311
~/nifti/t1/ah01111
~/nifti/t1/dd33333
~/nifti/bold/ab22311
~/nifti/bold/ah01111
~/nifti/bold/dd33333

such that files in the different t1 folders go into the t1/subjects_name folders; the same for files in the bold folders

How can a script can do this for me ??

thanks
Josselin

---

### Post by Vaphell on 2011-11-02
try this```
#!/bin/bash

cd ~/nifti
for f in */{t1,bold}/*
do
  dest="$( echo "$f" | awk -F/ '{ printf( "%s/%s", $2, $1 ) }' )"
  mkdir -p "$dest"
  cp "$f" "$dest"
done
```
i used cp to preserve files in old locations just in case something bad happens. Change cp to mv if you like.

---

