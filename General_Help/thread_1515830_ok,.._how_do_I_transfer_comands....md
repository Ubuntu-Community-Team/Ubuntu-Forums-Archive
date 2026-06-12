---
title: "ok,.. how do I transfer comands..."
date: 2010-06-22
forum: General Help
---

### Post by Zerocool Djx on 2010-06-22
My friend calls me and says he has a problem... Hes got like 48 short cuts put into the apps menu all running command lines in terminal that run short cuts to various programs.. transferring the programs not an issue cause they can all be transferred using APTonCD. but how can you transfer the shortcuts from the menus to another computer he's upgrading w/o typing them all over... Are all these stored in a file somewhere? how might it work?

---

### Post by Zerocool Djx on 2010-06-23
Bular?

---

### Post by 98cwitr on 2010-06-23
why not just do a static copy of / to the new drive using a live cd?

---

### Post by Zerocool Djx on 2010-06-23
What do you mean? like copy the whole OS? No that won't work,... Traditionally it might,.. but there is other things going on.. I really need to find files and folders for the drop down menus add-ons

---

### Post by Zerocool Djx on 2010-06-23
basically,.. where merging a few Linux OS systems programs into a single copy of Ubuntu...

---

### Post by konqueror7 on 2010-06-23
if i understand correctly you want to backup the Applications menu config plus the aliases (shortcuts) to the specific programs?

Application menu configs can be found here.
> /home/<user>/.config/menus

and aliases usually in *.bashrc* file located in your home folder.

---

### Post by john newbuntu on 2010-06-23
Assuming these were added through alacarte, you could try copying/merging files under:
/home/<userid>/.local/share/applications/
You should find files starting with "alacarte".  Pick the ones which do not have "Hidden=true".

---

### Post by Zerocool Djx on 2010-06-23
> **konqueror7 said:**
> if i understand correctly you want to backup the Applications menu config plus the aliases (shortcuts) to the specific programs?

Application menu configs can be found here.


and aliases usually in *.bashrc* file located in your home folder.


Bingo! Your awesome! 

*gives cookie*

---

### Post by Zerocool Djx on 2010-06-23
> **john newbuntu said:**
> Assuming these were added through alacarte, you could try copying/merging files under:
/home/<userid>/.local/share/applications/
You should find files starting with "alacarte".  Pick the ones which do not have "Hidden=true".

These not typical programs that kids would use,.. they have to be put in a certain way.. most of them not in that folder...

---

### Post by konqueror7 on 2010-06-23
oh! your welcome!...don't forget to mark this thread as solved...:p

---

