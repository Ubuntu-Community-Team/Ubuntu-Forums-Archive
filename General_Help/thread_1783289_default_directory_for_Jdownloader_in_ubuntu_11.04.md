---
title: "default directory for Jdownloader in ubuntu 11.04"
date: 2011-06-15
forum: General Help
---

### Post by Mike556 on 2011-06-15
hi all ^_^

i downloaded some files in the default directory of jdownloader i cant find the folder anywhere i had changed the directory to somewhere i could easily access but i forgot to move the files i had in the old download location.. foolish i know -_- but i have tried places> search for files but they dont appear =S

can someone please help me out? 

lots of thanks in advance =]]

---

### Post by ajgreeny on 2011-06-15
Hit Ctrl+H to show hidden folders just in case they are not showing, however they should still appear in the list if you use ```
sudo update db && locate <filename>
``` for a file that you are certain of the name.

PS:  Don't forget linux is case sensitive, so **Photo** is not the same as **photo** or **PHOTO**, so get the name right or use ```
locate -i <filename>
```

---

