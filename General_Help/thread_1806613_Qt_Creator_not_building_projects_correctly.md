---
title: "Qt Creator not building projects correctly"
date: 2011-07-17
forum: General Help
---

### Post by strattonbrazil on 2011-07-17
I'm having problems building my project in Qt Creator.  It was working fine, but sometime over the last few days I get build errors.  

If I clean out the project from the terminal, delete the Makefile, and run qmake, then go into the creator, it was it doesn't have the ui_sunshine.h file, which should have been created from the sunshine.ui form, right?  

If I make it at this point in the terminal, it seems to build the header files from the ui files fine, and I can run the executable, but if I try building in the creator, it then complains about some forward declarations.  Are they running different compilers or something?  I can stick with just the terminal for building for now, but I'd eventually like to use the debugger in the GUI every once and a while.

---

