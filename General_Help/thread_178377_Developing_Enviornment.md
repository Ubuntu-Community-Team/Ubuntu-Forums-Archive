---
title: "Developing Enviornment"
date: 2006-05-17
forum: General Help
---

### Post by darknecromancer on 2006-05-17
Hay, I moved to ubuntu to slackware cause i figured that it would be a better environment to program gtk applications in. I got everything setup that i can find, i have Anjuta 1.2.4 installed that im trying to use but whenever i try to compile just a simple gtk2.0 project i get the error "gtk/gtk.h: no such file found". I dont know a whole lot about linux, still fairly new, so i was hoping someone might be able to step me through diagnosing the process. I think it has to do with the environment not being setup right because when i tryed to manually install gtk and its said it found 2 different version of different stuff. I tried at one point to do a complete removal of all gtk stuff i could find and reinstall 2.0 but it said that it was also going to uninstall everything on my computer. Just hoping that someone has some ideas to help fix this.

Dark

---

### Post by mjm115 on 2006-05-17
Looks like you are not including the gtk header files in your source code.  Take a look at [this page]("http://anjuta.sourceforge.net/documentations/subpage/documents/C/anjuta-faqs/anjuta-faqs.html").  Scroll down to 5.1.  I hope this helps.

---

