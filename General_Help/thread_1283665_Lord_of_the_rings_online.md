---
title: "Lord of the rings online"
date: 2009-10-05
forum: General Help
---

### Post by BAMF1501 on 2009-10-05
OK so i bought lotro today and i installed all went goo dbut how the helll do i run it lol

---

### Post by c0mput3r_n3rD on 2009-10-05
The same way you installed it? I'm assuming you used WINE, so go to Applications -> WINE -> Programs -> NameOfGame, and click on it...

---

### Post by BAMF1501 on 2009-10-05
I have but doest work

---

### Post by fluffman86 on 2009-10-05
Open a terminal, then
```
cd .wine/drive_c/Program\ Files/
ls
```
to view which folders are available
```
cd name_of_LOTR_folder
```
(remember you can use <tab> to auto-complete long folders)
continue to cd and ls until you find the LOTR .exe
```
wine LOTR_FILE.exe
```
This should *NOT* be the setup.exe unless your install did not complete properly.

Now you should get some errors as to why LOTR isn't starting up.  You can post these here, but they will probably be more useful on a wine forum somewhere.

Also, a generic fix that sometimes work on some programs for me is to go into the wine config utility and set up a virtual desktop display, instead of having the game use a normal Ubuntu/gnome window.

---

### Post by Garyu on 2010-03-11
this is a really old topic, but I noticed that there isn't a reply here that offers a working solution, so I'm replying anyway in case someone searches and is trying to find an answer.

LOTRO has a windows-launcher that uses .NET technology, which isn't supported by Wine. Therefore, you have to use a custom linux-launcher. There is one that runs as a terminal script and another GUI version that I think is written in python. Both should be available from [http://www.winehq.org/](http://www.winehq.org/) if you search for LOTRO in their AppDB. 

So no, the above replies doesn't help because doing that will not start this particular piece of software. You should always look at the AppDB if a windows-program isn't running properly after installation (actually, it's best to look there before installing a windows-software).

---

