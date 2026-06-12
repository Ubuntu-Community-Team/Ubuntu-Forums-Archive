---
title: "Ubuntu n00b here, Question about Paths and Manpaths."
date: 2010-10-25
forum: General Help
---

### Post by Bakster10 on 2010-10-25
So I've just installed Ubuntu on a Virtual Machine and downloaded some software called G12. After running setup, the terminal displays the following:

Don't forget to add [directory name] to your PATH and a similar thing on the following for MANPATH. Further, the installation guide for G12 says "Once the SETUP script has finished running it will display a message informing you that the setup of the G12 core system is complete and that you should add the G12 bin directory to your PATH environment variable."

So what is this PATH stuff and why do I need it? And how do I add these directories to my PATH?

Thanks!

---

### Post by AlphaLexman on 2010-10-25
Depending on where > [directory name] you installed the program,
```
PATH=$PATH:[directory name]
``` will add the path.

MANPATH is a variable for linux to look for 'man' pages. A basic install should know where to put the help files.

**I would question your installation method if you are asking these questions!**

---

