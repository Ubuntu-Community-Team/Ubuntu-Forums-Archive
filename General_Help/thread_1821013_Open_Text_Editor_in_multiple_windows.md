---
title: "Open Text Editor in multiple windows"
date: 2011-08-08
forum: General Help
---

### Post by Benchrest on 2011-08-08
I sometimes have two similar files that one works and one doesn't. I would like to compare the differences.  But TEXT EDITOR opens two files in two tabs making it impossible to compare the data side by side.

Is there a way to make Text editor open a separate window for each file? Browsers usually have such an option to choose multiple windows or tabs but I can't find away to do this with Text editor.

---

### Post by SalHelder on 2011-08-08
If you are using gedit try the command:

gedit --new-window

---

### Post by Benchrest on 2011-08-08
That does work, but from terminal command line. The text editor is gedit.  I guess I am looking for an option to set it permanent to always open a new window and not have to go to terminal.  But now I bet it is possible. If it can be done from command line there probably is a way.  It is not in preferences.  I guess I just want to be able right click on a file in nautilus and select text editor and have the file open in a new window without going through terminal.  The default is tabs and I bet it can be changed to windows.

---

### Post by Simian Man on 2011-08-08
I have an even better suggestion: try meld.  It is a graphical diff program that is great for highliting differences in large files.  It shows you the differences side by side.

---

### Post by Benchrest on 2011-08-08
I found the answer and it is so simple it's scary.  After opening the second file, right click on one of the tabs and select open in new window. It will then open the entry for that tab in a new window.

---

### Post by Sotanaht on 2011-08-08
I'm pretty sure you can also drag the tab outside the window and it will open it in a new window.  At least that works in most programs.

---

