---
title: "Lost all documents when changing language!!"
date: 2011-03-10
forum: General Help
---

### Post by Spekke on 2011-03-10
I lost all my documents (e.g. Music, Documents, Pictures,... ) when I changed the language.
Is there any way to recover them???

greetings Spekke

---

### Post by An Sanct on 2011-03-10
How did you change the language? Did you do a reinstall?

---

### Post by ajgreeny on 2011-03-10
Are you sure they are lost?

In terminal type ```
ls -laR /home/$USER/ | less
``` and use the page down key to move from page to page.

I suspect the files will still be there, but if not under your user name try ```
ls -laR /home/ | less 
```  just in case the files are now in another username's home for some weird reason.

---

### Post by Spekke on 2011-03-10
Thanks it worked, found them back :D
for some weird reason the 'old' directories were still there, but he didn't show them. really weird :p but anyway, got them back now :D

---

