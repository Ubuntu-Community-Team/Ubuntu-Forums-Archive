---
title: "GIT help"
date: 2012-07-09
forum: General Help
---

### Post by nathanv221 on 2012-07-09
hi all,
i am trying to commit a change so i can pull from the origin but git won't let me commit the change. i would be happy to undo the change as well but git won't allow that ether. 

heres what i get when i ask for "git status"
#
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#    new file:   Applications/DICOMSeriesConverter/DICOMSeriesConverter.cxx~
#

i also have untracked files but i don't think they matter so i wont waste your time with them.

when i tell git to "commit Applications/DICOMSeriesConverter/DICOMSeriesConverter.cxx" i get this
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#    Applications/DICOMSeriesConverter/DICOMSeriesConverter.cxx~
nothing added to commit but untracked files present (use "git add" to track)

if i use git reset HEAD to unstage the commit it looks successful but gos back to the same status.

any ideas? i don't care whether the file is changed or not just so long as it still exists.

---

### Post by spjackson on 2012-07-09
Note that the name of the added file reported by git status ends in ~
So
```
git reset Applications/DICOMSeriesConverter/DICOMSeriesConverter.cxx~
rm Applications/DICOMSeriesConverter/DICOMSeriesConverter.cxx~

```

---

