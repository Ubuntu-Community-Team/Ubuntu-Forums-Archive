---
title: "frostwire and dual boot"
date: 2006-03-27
forum: General Help
---

### Post by mandy on 2006-03-27
i have a dual boot machine and have installed frostwire in ubuntu and in xp, and have the shared folder on a shared fat32 partition, and have both installations pointing to the same shared folder, but i can't seem to get it so that they share an incomplete folder - my ubuntu install keeps the incompletes on the shared partition but windows has created one in c:/home/common/incomplete (the root that ubuntu should use as common is what i've called the shared partition in ubuntu) - and starts to download my incomplete files, but from scratch, and if i then go back to ubuntu it starts them from scratch again!

anyone know how i can have it so that i can complete a download form one os to the other?

---

### Post by xiaoxin on 2006-03-28
But my experience is if you change the saving location of your files in the windows frostwire it will automaticly create a new incomplete folder in the same location as the saving folder.
Maybe you should recheck your frostwire settings.

---

### Post by mandy on 2006-03-28
it has but in the wrong place - its created it on my windows partition using my linux root (obviously linux saved where my shared files were and when pointed to by the windows one must have had a root to incomplete folder, or the root is saved in one of the files in the incomplete folder but when windows reads it its wrong as they operate differently for windows i want it to be f:/incomplete (as it is for linux) and though i have my shared folder as f:/shared my incomplete is c:/home/common/incomplete - in frostwire it states the entire root to the incomplete file)

its only when i use the same folder for shared i get this issue (if i use any other folder it creates the incomplete in the same place), and i guess its because the root has already been set by ubuntu, and so the incomplete is pointed to by some setting or other somewhere (i guess downloads.bak or .dat though they are in the incomplete folder - i guess it follows the path to find the incomplete file ie /home/common/incomplete and windows reads it as c:/hom....)

---

### Post by xiaoxin on 2006-03-28
ok i understand your problem now.
I think what you want is impossible, or you should edit the file which has the infomation where frostwire saves the file every time you switch os.

---

### Post by mandy on 2006-03-28
that was the conclusion i was reluctantly coming round to too

shame unless anyone else has a fantabidosie idea

---

### Post by xiaoxin on 2006-05-09
although you could use a startup script in both Os's to edit that file

---

