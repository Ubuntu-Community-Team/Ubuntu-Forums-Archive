---
title: "VBA express"
date: 2010-09-17
forum: General Help
---

### Post by Kareta on 2010-09-17
following [this]("http://ubuntuforums.org/showthread.php?t=87421") thread when I got this error after running:

```
[FONT=monospace]make[/FONT]
```error:

```
kareta@ubuntu:~/FLU_2.14$ make
=== making src ===
make[1]: Entering directory `/home/kareta/FLU_2.14/src'
Compiling Flu_Combo_Tree.o...
In file included from /home/kareta/FLU_2.14/FLU/Flu_Combo_Tree.h:20,
                 from Flu_Combo_Tree.cpp:23:
/home/kareta/FLU_2.14/FLU/Flu_Tree_Browser.h:349: error: extra qualification ‘Flu_Tree_Browser::’ on member ‘inside_entry_area’
/home/kareta/FLU_2.14/FLU/Flu_Tree_Browser.h: In member function ‘unsigned int Flu_Tree_Browser::Node::remove(const char*)’:
/home/kareta/FLU_2.14/FLU/Flu_Tree_Browser.h:1081: error: cast from ‘Flu_Tree_Browser::Node*’ to ‘unsigned int’ loses precision
make[1]: *** [Flu_Combo_Tree.o] Error 1
make[1]: Leaving directory `/home/kareta/FLU_2.14/src'
```

---

### Post by kalos on 2010-09-17
First result on [google]("http://lmgtfy.com/?q=error%3A+cast+from+Flu_Tree_Browser%3A%3ANode*+to+unsigned+int+loses+precision") is a related bug and the fix:
[http://code.google.com/p/animata/issues/detail?id=38#c5](http://code.google.com/p/animata/issues/detail?id=38#c5)

If you apply the changes from comment #5 to your version of the code, you should be able to build.

The easy way to do that is put the changes in a file to make a patch and then apply it with the unix patch program.

Call the file precisionfix.patch and run ```
patch --dry-run < precisionfix.patch
``` If that gives positive output, then do it again without --dry-run.

---

