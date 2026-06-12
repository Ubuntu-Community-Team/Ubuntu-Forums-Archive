---
title: "help using sed and awk"
date: 2010-12-18
forum: General Help
---

### Post by roobinatube on 2010-12-18
Hi, i hope someone can help me here.

I'm using scilab as an alternative to matlab, and although there is a converter from .m files to .sci files, there isnt one the other way around. Seeing as though the differences in code are small, I figured I could set about making a script to run through, that searched for parts of scilab code and changed it to matlab code. If anyone is interested the differences are [here]("http://www.scilab.org/product/dic-mat-sci/M2SCI_doc.htm").

Here is an example

MATLAB: acot(A)
SCILAB: atan(1 ./A)

It is easy to use sed to search for atan(1 ./A) and replace with acot(A), the problem is that 'A' might not be 'A', it could even be a function of its own. Is there a way to make 'A' into a field, then use it again to replace the text around it?

It would be helpful if you explained the answer, if you had time, im a chemical engineer, not a software engineer... I like learning but my skills are rather primative at the moment!

Many thanks
Roo

PS my example of acot is probably not a good one, I think both of these would work in matlab... but i dont have matlab here to test it... I figure a solution to that could be applied to others too.

---

