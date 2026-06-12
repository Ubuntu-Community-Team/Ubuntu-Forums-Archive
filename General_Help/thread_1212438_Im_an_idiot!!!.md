---
title: "Im an idiot!!!"
date: 2009-07-13
forum: General Help
---

### Post by FetalShinobi on 2009-07-13
someone please help me! i was browsing my folders and i was in the home folder. i guess i got a little too happy pressing the delte button cause i ended up sending the DESKTOP folder to the trash! now i didnt have much in the desktop but i did have a bunch of comic books i had just downloaded and for some reason i cant seem to be able to restore the folder to its original location!!!! what do i do?

---

### Post by H4F on 2009-07-13
Look in trash folder.
if no. the easiest way is to download them again

---

### Post by FetalShinobi on 2009-07-13
the folder is in the trash but it wont let me restore it or drag it out. it says "trash contents cant be modified" and i really dont want to have to sit here and download 1.4 gb of comics all over again. :'(

---

### Post by Viva on 2009-07-13
Can you see the contents of the folder in trash?

You can find the trash content by opening ~/.local/share/Trash in nautilus.

---

### Post by FetalShinobi on 2009-07-13
yes....i copied them and im trying to paste them back to the desktop but the file operations pop up doesnt show any progress.....

---

### Post by tqx on 2009-07-13
Open a terminal, run this command:

```

cp -R ~/.local/share/Trash/files/* ~/Desktop

```

---

### Post by H4F on 2009-07-13
Did you try use restore button in trash ?

---

### Post by FetalShinobi on 2009-07-13
yes and nothing. i didnt try to use the terminal code cause i already copied everything from the trash back to its respective folders. thing is how do i delete those doubles that i have on the trash then?

---

### Post by H4F on 2009-07-13
delete everything in thrash:
rm -R ~/.local/share/Trash/files/* 

you might need sudo if you will not have enough permissions

---

