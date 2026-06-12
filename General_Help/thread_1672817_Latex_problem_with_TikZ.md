---
title: "Latex problem with TikZ"
date: 2011-01-21
forum: General Help
---

### Post by NameThatMeetsAdmStandard on 2011-01-21
Hello, I have a problem with using TikZ in Latex, namely I get an error compiling this:

```
\begin{tikzpicture}
\matrix [matrix of math nodes]
{
a_8 & a_1 & a_6 \\
a_3 & a_5 & |[red]| a_7 \\
a_4 & a_9 & a_2 \\
};
\end{tikzpicture}
```the error I get is:

> ERROR: Package pgfkeys Error: I do not know the key '/tikz/matrix of math nodes' and I am going to ignore it. Perhaps you misspelled it.Can anybody tell me what I can do to solve this?


Some more information:
The latex on my system is up to date, in fact I just installed it today.
A "sudo apt-get install pgf" also tells me that my pgf package is up do date.
And the code above should work, 
in fact I just copied it from the pgf manual I downloaded an hour ago (p205).


thanks in advance.


Edit: Wait, what did I do so that this is displayed as solved??

---

