---
title: "is there specific location for the installed programs?"
date: 2011-01-09
forum: General Help
---

### Post by karpay on 2011-01-09
Dear all!

I'm new to ubuntu.

Yesterday, I downloaded qt and gcc by using "synaptic package manager" tool.

Where does those programs intstalled?

Well, in windows the programs are installed in c:\Program Files folder. Similarly, is there a specific folder that the newly installed programs are placed?

Thank you for the help...

Best regards.

---

### Post by Quackers on 2011-01-09
They are often installed to /usr/bin I believe.

---

### Post by 3rdalbum on 2011-01-09
GCC is a command-line tool for compiling software; it is invoked by the "make" command when you're compiling a program. You don't need to know where GCC is. It's probably sitting in /usr/bin, but as it's a command-line program and it sits in the $PATH, you don't need to specify a location or go there and double-click it; just use 'gcc' on the command-line if you know how, or just run 'make' for the software you want to compile.

Qt is not even a program, it's a set of libraries. You don't need to know where the libraries are; as long as the programs that need the libraries can find them, that's all that matters. Qt is probably in /usr/lib.

In general, files are installed to locations where they can be found by relevent systems. For instance, when you install a program it doesn't just spread all its contents out into a single directory. It installs icons in one of the system directories for icons, libraries into a system directory for libraries, manual pages in the system directory for man pages, etc. You don't need to worry about this - programs will create launchers in your menu if they are GUI programs, and will be able to be run by just typing their name in the terminal if they are command-line programs.

---

### Post by oopsie on 2011-01-09
Linux tends to explode programmes, so they get spread all over the place.

If you want to see where, find your installed programme in the synaptic package manager, right click what you installed, select "properties" then the "installed files" tab. You should find all the directories it installed to.

---

### Post by karpay on 2011-01-09
Dear oopsie and 3rdalbum thank you very much for your help!

It is pretty much helpful :)

Best regards...

---

