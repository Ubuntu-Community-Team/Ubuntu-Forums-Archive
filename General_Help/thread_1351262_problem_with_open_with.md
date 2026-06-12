---
title: "problem with open with"
date: 2009-12-10
forum: General Help
---

### Post by hwttdz on 2009-12-10
So I'm attempting to open a file with a program, and at the command line
programname filename
works fine, however if I right click open with /path/to/programname the program opens up, loads the file then quits out.  Because I can't debug this on the command line I don't know what to do.  

So the problem is that open with opens the file then immediately quits, and the expected behavior is that it opens the file and allows me to do what I want in the program before closing.

---

### Post by gordintoronto on 2009-12-10
Is the program too big to include in your message?

By the way, there is a Development and Programming forum.

---

### Post by hwttdz on 2009-12-10
The program is too large to include in a post (it is a large binary and would not be helpful).  This is neither a programming nor a development question, therefore I did not think it proper to post in a forum devoted to those topics.

Additional information which you may have intended to ask for: Programname is VMD, which is visual molecular dynamics published by the University of Illinois.  Filename is N26Aa.pdb, which is the ligand of the structure 2C60 published in the PDB (protein data bank, maintained at Rutgers, UCSD, Brookhaven and possibly others).  

My question deals with gnome's graphical interface and the exact command which is executed when I select open with.  I am hoping that someone is able to enlighten me on this topic as I am unable to find documentation.  I sort of figured when one selected open file with, the command executed was in general "programname filename", which is why I am confused, because "programname filename" produces the correct behavior on the command line however it doesn't produce the correct behavior here.

---

### Post by hwttdz on 2009-12-10
The program, despite being graphical, is considered command line (by I don't know which powers that be), but 

"gnome-terminal -x programname"

as the custom command did the job.

---

