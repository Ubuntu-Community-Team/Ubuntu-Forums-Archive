---
title: "LaTex stops working (but not Lyx)"
date: 2011-10-01
forum: General Help
---

### Post by Minguo on 2011-10-01
Hi, earlier this year I installed LaTex to work on a resume.  No problems, got it working fine.

Today when I went to update it, the program does not function properly. running

```
tex resume.tex
``` produces an 
```
! Undefined control sequence.
``` error for every line of code and outputs a .dvi full of junk.

If I  try to create a test file with nothing in it but 
```
%test.tex test

\documentclass{article}
\begin{document}
\title{How to do stuff}
\end{document}
```

I still get the undefined control sequence error for every line of code. So I figured I must have corrupted a file somewhere or somehow.  I completely removed every tex package (using synaptic) and reinstalled it. 

But the issue repeats itself, even after reinstalling.   What in the world could I have done in this case?

Also, Lyx works and produces correct output, but not calling tex directly.

---

