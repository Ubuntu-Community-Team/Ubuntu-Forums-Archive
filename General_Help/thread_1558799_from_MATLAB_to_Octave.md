---
title: "from MATLAB to Octave"
date: 2010-08-22
forum: General Help
---

### Post by sammy0131 on 2010-08-22
[FONT=Arial][SIZE=2]Hi, I'm trying hard to migrate on Ubuntu and started changing the scripts that i wrote for MATLAB to those for Octave.

I found that I've got a different result when I'm running "corr2" function in MATLAB and
Octave.

I use the same size of two matrices and then used as:

R = corr2(matrixA, matrixB);

in MATLAB R is one correlation coefficient just as:
[http://www.mathworks.com/access/help...ges/corr2.html]("http://www.mathworks.com/access/helpdesk/help/toolbox/images/corr2.html").

However, when I run the same script in Octave, the answer turns out to be a
matrix. For example is I used 5000x600 matrix, the R is 600x600.

I'd very much appreciate if anyone can explain to me why this is happening.

So far it seems like using Octave 100% is far away...but MATLAB is very expensive.
[/SIZE][/FONT]

---

