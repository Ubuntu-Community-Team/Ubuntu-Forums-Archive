---
title: "Rename multiple files recursively with folder name"
date: 2011-10-24
forum: General Help
---

### Post by publicjo on 2011-10-24
Dear all,

I have not found a relevant solution to my issue on the forums:

I have files with identical names (FA.nii) which are in several folders like this:
/home/toto/subject1/stand/FA.nii
/home/toto/subject2/stand/FA.nii
/home/toto/subject3/stand/FA.nii
/home/toto/subject4/stand/FA.nii
/home/toto/subject5/stand/FA.nii

I would like to move them in a single directory and rename them with their original folder name so to get them like this:
/home/toto/process/FA_subject1.nii
/home/toto/process/FA_subject2.nii
/home/toto/process/FA_subject3.nii
/home/toto/process/FA_subject4.nii
/home/toto/process/FA_subject5.nii

How can I proceed ?

Thanks,
Josselin

---

### Post by Vaphell on 2011-10-24
```
cd /home/toto/; mkdir process; for f in */stand/FA.nii; do cp -v -- "$f" "process/FA_${f%%/*}.nii"; done
```
i used cp so you have original files just in case, you can use mv instead

---

### Post by publicjo on 2011-10-24
Thanks, it works perfectly well !
:p
Josselin

---

