---
title: "i can't save file"
date: 2009-07-01
forum: General Help
---

### Post by ceycey60 on 2009-07-01
i want to save my php files after written on geany

i have opened the geany and i have written my codes, but i can't save it (my index.php file) under the filesystem, www directory.i receive an error message from geany like this :
[B]
"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."
[/B]
note : i am root,why can't i save?

---

### Post by michy99 on 2009-07-01
Are you sure you are root? Try saving the file to you home directory, and then move it to where it needs to be using sudo.

---

### Post by wojox on 2009-07-01
Ya that's weird if your root and don't have permission.
When I edit/write php scripts I open a terminal and sudo gedit.
You could try that for geany also.

---

### Post by ceycey60 on 2009-07-01
thank you for helps, i've solved problem

i've opened terminal and sudo geany,i can save my files with geany now...

and netbeans can be open like sudo geany ? i tried but i cant succeed

---

### Post by ceycey60 on 2009-07-01
yes i have succeeded

i open "sudo fullpathofnetbeans"


thanks for everyting

---

