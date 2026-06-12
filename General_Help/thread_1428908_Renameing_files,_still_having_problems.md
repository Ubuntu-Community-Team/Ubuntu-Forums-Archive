---
title: "Renameing files, still having problems"
date: 2010-03-13
forum: General Help
---

### Post by cbaughman on 2010-03-13
I'm still moving large numbers of files around and as i'm still trying to figure out some basic scripting I'll need some more help. The script below will move each file in the directory with the avi extension into a new directory of the same name. 

My next challenge is a little different but i expect i can adapt this script to do what i need. I need to rename each file in a directory to the same name as the directory. The Files all have garbage names but the directories are named properly. Oh and i need to keep the avi file extension.

Any help would be great. Thanks!


for file in *.avi; do 
  mkdir "${file%.avi}"
  mv "${file}" "${file%.avi}"
done

---

