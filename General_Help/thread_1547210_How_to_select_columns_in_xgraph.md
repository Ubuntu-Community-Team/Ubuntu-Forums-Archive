---
title: "How to select columns in xgraph"
date: 2010-08-06
forum: General Help
---

### Post by jestinjoy on 2010-08-06
I am using xgraph with ns2. Is there any provision in xgraph to select columns. Man page didnt say anything about it.

---

### Post by jestinjoy on 2010-11-03
Searched net but couldnt find any suetable answer so moved to gnuplot. It has options to select which cloumns are used as the x and y axes. 

Example:

gnuplot> plot "force.dat" using 1:2 with line

Plots the file force.dat with column 1 as x axis and column 2 as y axis using line representation. We can specify column in whatever order we like. :popcorn:

---

