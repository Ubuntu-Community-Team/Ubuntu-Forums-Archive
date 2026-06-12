---
title: "merge subfolders"
date: 2010-01-28
forum: General Help
---

### Post by Aluxander on 2010-01-28
say I had ts file setup:
-Folder
--Folder1
---File1
---File2
--Folder2
---File3
---File4
--Folder3
---File5
--Folder4
--File6

etc, what command could I run in the terminal to put all the subfiles into the root folder, Folder. obv that was an example, so just a command that goes in every subdir and moves all the files up one folder, the subfolders dont have subfolders

---

### Post by bluefrog on 2010-01-28
find Folder -type f -exec mv "{]" Folder/ \;

---

### Post by amauk on 2010-01-28
typo above,

find Folder -type f -exec mv "[COLOR="Red"]{}[/COLOR]" Folder/ \;

---

### Post by Aluxander on 2010-01-28
thank you :D

---

