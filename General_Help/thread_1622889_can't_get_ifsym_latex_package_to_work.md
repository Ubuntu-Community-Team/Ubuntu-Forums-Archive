---
title: "can't get ifsym latex package to work"
date: 2010-11-16
forum: General Help
---

### Post by Nimridil on 2010-11-16
Hello fellow Ubuntu users.
I was just going to use the pulse symbols from ifsym for one of my physics lab reports when I figured that I don't have ifsym installed. So, I went to the CTAN site [http://www.ctan.org/tex-archive/fonts/ifsym/](http://www.ctan.org/tex-archive/fonts/ifsym/) and got it. Then I found this page to explain me where to place the files. [http://liyi.freeshell.org/computer/tex/install-ifsym](http://liyi.freeshell.org/computer/tex/install-ifsym) That unfortunately had no effect. (I did run sudo texhash). I rummaged a bit about the forum and found this thread (I'm using texworks myself) - [http://ubuntuforums.org/showthread.php?t=1541945](http://ubuntuforums.org/showthread.php?t=1541945) That didn't help either. Following the post, I put files in /usr/share/texmf-texlive/tex/latex/ but alas in vein. I even tried to copy the files to a bunch of other similar looking tex directories in /usr/local/share/ and /usr/share/ but also with no result. Finally I downloaded the texlive-fonts-extra package from Synaptic, but my tex file still doesn't want to compile, in neither texworks nor from terminal using the pdflatex command. It doesn't throw an error at the line \includepackage{ifsym}, but at the symbol itself. I was originally going to include the \FallingEdge but to make sure I tried other symbols not pertaining to pulses from the same package and non of them were recognized.:mad:
Does anybody know what I could do to make that package recognizable by latex compiler?

---

### Post by C. M .Hughes on 2010-11-27
I don't know if this will help or not, but I use
```
sudo mktexlsr
``` instead of texhash

---

### Post by costis on 2013-01-30
I have exactly the same problem. I do not receive any kind of error after using ```
\usepackage{ifsym}
```, but when I use a symbol, like \Sun I get ```
! Undefined control sequence.
l.372 \Sun
```

Did you find a solution? Anybody? (using ubuntu 12.10)

---

### Post by Impavidus on 2013-01-31
Reading the manual (ifsym.ps, included in the download from ctan) pays off.> [FONT=Courier New]weather[/FONT] definiert Befehle für Wettersymbole (Abschitt 4).
[FONT=Courier New]electronic[/FONT] definiert die elektronischen Symbole (Abschitt 5.4).The fact it's in german may be a small hurdle for some of us, so this is your solution. For costis, try using```
\usepackage[weather]{ifsym}
```Nimridil can use ```
\usepackage[electronic]{ifsym}
```

---

