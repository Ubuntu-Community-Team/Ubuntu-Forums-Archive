---
title: "latex problem: amsmath align environment not working on lucid lynx"
date: 2010-10-27
forum: General Help
---

### Post by _mjh_ on 2010-10-27
using the amsmath package with texlive on lucid lynx, a simple

[FONT=Courier New]\begin{align}
 x &= 1
\end{align}[/FONT]

gives the following error:  

[FONT=Courier New]! Missing # inserted in alignment preamble.
<to be read again> 
                   \crcr 
l.424 \end{align}[/FONT]


the same .tex file works fine on other another (unix) machine with pdfeTeX.  I had no problems like this with a previous computer running Hardy Heron.

thanks,
_mjh_

---

### Post by cugat on 2010-10-27
It might be the editor you're using. I sometimes have trouble with one but not another (but I know what you mean about latex files working  on one machine and not another). I use both Kile and Texworks, but there are certainly others. Might as well give those a shot.

I pasted your equation into a latex file I have and it works, so it's not a code problem. Assuming your example is just an example, you might be better off using the {equation} or {eqnarray} environment rather than {align}. Or if it is just a simple x=1, why not just 

$$
x=1
$$

---

### Post by _mjh_ on 2010-10-29
thanks for your reply cugat.  I am using xemacs but calling latex (pdflatex) from the command line...  so there should be no editor issues (but, can't hurt to investigate this further).

for the time being I think I may just stick with equation and eqnarray as you suggest, although align really does a better job for what I am doing. 

thanks
_mjh_

---

