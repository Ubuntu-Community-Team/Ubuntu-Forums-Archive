---
title: "Strange search for files  engine"
date: 2010-02-27
forum: General Help
---

### Post by farus.pri.ee on 2010-02-27
hello everybody
I already saw it before but today it is need and it is not work correctly or it is working strange.
Explanation. I have folder with php files many of them has key words for example text_library_connection (i know it exactly because I found it from file to file) but.. I try to find it with places->search for files->
Name contains : nothing just space or *.php or *.*
contains text : text_library_connection 
and search result is nothing! 
But three files at least in this directory have this phrase...
How to search it correctly???

---

### Post by hwttdz on 2010-02-28
Well I can't speak for the gui, but on the command line you can just:
cd (to directory of interest)
grep -l "text_library_connection" *.php

and you'll get a list of files containing your phrase.  I'm sort of a big fan of grep/find as oppose to the gui because you know _exactly_ what it's doing and you can be as picky as you want.

---

### Post by coldraven on 2010-02-28
The Nautilus find files function is useless!
Download Krusader and use that instead. Krusader is a two pane file manager like Total Commander for windows.

---

