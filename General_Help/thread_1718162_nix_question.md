---
title: "*nix question"
date: 2011-03-30
forum: General Help
---

### Post by lapishc on 2011-03-30
Hello Ubuntu world,

Linux question.  I am trying to horizaontally concatenate two columns of data from 2 separate files A.dat and B.dat.  I have tried using the 'cat' command bu that vertically concatenates these data. 

For instance

A.dat= 
1
1

B.dat= 
2
2

cat A.dat B.dat > C.dat
C.dat=
1
1
2
2

But what I would like is 
?cat A.dat B.dat > C.dat
12
12

Any insight is much appreciated and sorry if this is out of the scope of this message board!

---

### Post by lapishc on 2011-03-30
Solved my problem...

I really, really love linux....so cool. 

paste -d"," A.dat B.dat > C.dat

---

