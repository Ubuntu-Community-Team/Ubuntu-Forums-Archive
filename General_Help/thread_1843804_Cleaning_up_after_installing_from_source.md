---
title: "Cleaning up after installing from source"
date: 2011-09-14
forum: General Help
---

### Post by n125 on 2011-09-14
Heya

I successfully compiled and installed a program from source code (Stellarium, to be specific; it's in the repositories but I wanted a newer version). So with that done, I was wondering if there are any options I can take to clean up after the procedure, if even necessary.

1) Which source files can I safely delete? I understand that I won't be able to uninstall the program easily ('make uninstall') if I remove certain files, but I don't know which ones. I'd like to have this option, but I don't want to keep any unnecessary source files. I have a source directory with all of the source files that I pulled with bzr, and then a build directory populated with files after executing the command 'make'.

2) I had to install some build dependencies I didn't have, like libqt4-dev and a few others that I can't remember. Is there any easy way to remove some of the ones I no longer need? 'sudo apt-get autoclean && sudo apt-get autoremove' both say there's nothing to delete.

Thanks!

---

### Post by ibutho on 2011-09-14
You can use "make clean" after running "make install". That should remove any object files created during the build process. If you delete the directory where you built from, you cannot uninstall by running "make uninstall", so I usually just keep it.

---

