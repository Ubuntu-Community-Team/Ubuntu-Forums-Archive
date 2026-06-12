---
title: "File/Folder comparison program"
date: 2009-09-01
forum: General Help
---

### Post by Zalbor on 2009-09-01
Hello all,
I'd like to ask if anyone knows a program that can do file and folder comparisons. In windows I've found one called "beyond compare", which basically asks you to point at two files or folders.
In the case of folders, it shows you which files are newer on one side or don't exist at all etc, and in the case of files it shows you extra lines in one or differences in others.

Do you know of a similar linux program?

---

### Post by DaithiF on 2009-09-01
from the command line: diff

if you want a graphical version, meld is one I've heard of frequently.
```
sudo apt-get install meld
```

---

### Post by StuartN on 2009-09-01
I have been using krusader more than meld recently. Krusader displays two panes on two directories and performs a directory (with recursive subdirectory) comparison to produce a list of changes required to synchronise. You can accept this list, choose only left-to-right, right-to-left, newer files, absent files etc - or export the list into a pane to manage the files in your own way. Unlike meld, you can easily browse around and investigate / deal with discrepancies like renamed directories, which is great when synchronizing music libraries or photograph archives.

It is in the repositories and runs well in gnome, although some of the kde tools it expects are not installed by default.

---

### Post by eumetaxas on 2009-09-01
i use that one
[http://www.sourcegear.com/diffmerge/](http://www.sourcegear.com/diffmerge/)

It is free but not open-source. Works perfectly under Ubuntu

---

### Post by Zalbor on 2009-09-03
Thanks for all your suggestions! :)
I decided to go with meld in the end, I like the interface best and while it's simple it behaves in the way I like.

---

### Post by six^letters^digits on 2010-01-06
sudo apt-get install meld
[http://meld.sourceforge.net/install.html](http://meld.sourceforge.net/install.html)

from:  file compare tool (GUI)
[http://ubuntuforums.org/showthread.php?t=336933](http://ubuntuforums.org/showthread.php?t=336933)    -->

sudo apt-get install kdiff3
[http://kdiff3.sourceforge.net/](http://kdiff3.sourceforge.net/)

sudo apt-get install xxdiff
[http://furius.ca/xxdiff/](http://furius.ca/xxdiff/)

sudo apt-get install tkdiff
[http://sourceforge.net/projects/tkdiff/](http://sourceforge.net/projects/tkdiff/)
[http://wiki.tcl.tk/3773](http://wiki.tcl.tk/3773)

:KS

---

