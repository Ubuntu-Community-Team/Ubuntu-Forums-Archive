---
title: "Help uninstalling a tutorial program"
date: 2011-06-10
forum: General Help
---

### Post by Joshua0317 on 2011-06-10
Hello all,

I'm pretty new to Linux.  I was running a tutorial that was showing how to install programs from downloaded tar.gz files.  

In the commands, I used ./configure --prefix=$HOME/programname

This installed it in my home folder.  The tutorial didn't include instructions on how to remove the program.  Since it is useless I would like it gone.  

Question:  If I just run rm -rf on the josh/programname folder will this effectively uninstall it?  Or did it install files other places.

Other facts:  It didn't come with an uninstall so make uninstall is useless.  I ran ./confiure from the same place I extracted the files from which what my Downloads directory.

Any help would be great, more so that it will teach me where things are stored when I install something

---

### Post by nitstorm on 2011-06-10
Is there an uninstall.sh that came along with the download? or something similar to that effect?

---

### Post by Joshua0317 on 2011-06-10
Not that I can find.  There is an install.sh, but nothing in the files that could uninstall.

---

### Post by nitstorm on 2011-06-10
Run ```
locate *pgm_name*
```
See if the program has files installed in other places or just the home folder. Then you can delete the file locations at different locations or one location (depending on the output of the code) and you have effectively uninstalled the program.

---

### Post by Joshua0317 on 2011-06-10
So, just to clarify, deleting all the files a program saves on your computer is the same as uninstalling it correct?  I don't know why it wouldn't be the same, but it is better to ask than to not ask and mess something up.

---

### Post by nitstorm on 2011-06-10
Yes, I screwed up big time coz of compiz a long time back and a kind person on UbuntuForums helped me delete every bit of Compiz off my comp and that is ultimately uninstalling the program.

---

### Post by Joshua0317 on 2011-06-10
Thanks a ton.  It was a pretty simple unit converter program and I am pretty sure all it did was create the folders in my /username directory so I just removed all of them.  Using the locate units all I found was a manual entry for units that was part of a different program.  

Thanks again.

---

### Post by WorMzy on 2011-06-10
If you ran the install script as your user (e.g. you didn't use "sudo"), and the install script ran without errors, then it will only have placed files in your home folder, since that is the only place (aside from /tmp) that you are "allowed" to install files to. Deleting these files will "uninstall" the program.

---

### Post by nitstorm on 2011-06-10
Cool :)

---

