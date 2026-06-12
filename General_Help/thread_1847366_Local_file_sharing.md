---
title: "Local file sharing"
date: 2011-09-20
forum: General Help
---

### Post by Sidney232 on 2011-09-20
What's the best way to implement file sharing (collections of music or photos etc.) between users of the same machine? Use a '/home/shared' folder? Or something more complicated? There seems to be a lot about sharing across networks but not between local users.

---

### Post by spiky001 on 2011-09-20
Do these help
[http://ubuntuforums.org/showpost.php?p=413262&postcount=3](http://ubuntuforums.org/showpost.php?p=413262&postcount=3)

[http://brainstorm.ubuntu.com/idea/4397/](http://brainstorm.ubuntu.com/idea/4397/)

---

### Post by brucehohl on 2011-09-20
By default users can read files of other users since file are created with permission setting 644 (read-write to owner; read to group; read to all others). In Nautilus Right click on a file and select Properties then the Permission tab to see these settings (or in a terminal run 'ls -l'). 

Thus, for read only 'sharing' just navigate to the file and open. Set a Nautilus bookmark if you plan to return often. For read and write access to a file the Nautilus permissions must be adjusted. For creation rights the directory permissions must be adjusted.

---

