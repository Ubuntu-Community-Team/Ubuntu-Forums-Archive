---
title: "gedit latex plugin: open with evince command"
date: 2009-11-29
forum: General Help
---

### Post by VCoolio on 2009-11-29
Hi, sorry to start a thread for this, but I lost the command behind the Latex -> PDF menu entry for the gedit latex plugin. Could you provide me with the default command(s) listed in edit > preferences > plugins > gedit latex plugin > configure plugin > tools > latex->PDF > properties? Thanks in advance (I don't want to reinstall the plugin because I've configured some more and also I don't know if that would solve it. I found an [old forum thread]("http://ubuntuforums.org/archive/index.php/t-211936") with some commands to enter, but they didn't work; I guess the variables were changed; or possibly I did something wrong).

---

### Post by XCan on 2009-11-30
I have changed my default PDF batch job, but if you merely were referring to opening the compiled document with evince it's ```
 evince "%e.pdf" & 
```

---

### Post by VCoolio on 2009-11-30
Thanks for replying, but evince keeps telling me: no such file or directory. Now I always get impatient with errors like this, so I reinstalled the plugin is this is how it was:
```
rubber --inplace --maxerr -1 --short --force --warn all --pdf "$filename"
gnome-open "$shortname.pdf"
```

](*,) I thought $shortname would be the filename without path, but it's filename without extension. My bad, should have tried it; anyway, problem solved.

---

### Post by hugmenot on 2009-11-30
By the way, you can remove the gnome-open in there. Evince in Karmic reloads PDF files automatically when they change on disk. There is no flicker when it dos it and the viewport doesn&#8217;t move.

---

### Post by VCoolio on 2009-11-30
oow, that's neat. Thanks for pointing that out, will try. But if evince isn't open yet it doesn't work of course; maybe use a script to check if it's open, or if it's open just use the menu entry below that also exports to pdf. Anyway, opportunities arise.

Maybe it's not so clever to ask now I marked the thread as solved, but does anyone happen to know why the embedded gedit preview doesn't show greek text (from betacode) while evince does? I spent half an hour yesterday to get greek text going when I discovered I did it right all the time only the preview doesn't show it.

to try yourself:
```
\documentclass[12pt,a4paper,oneside]{book}
\usepackage{eufrak}
\usepackage[utf8x]{inputenc}
\usepackage[english]{betababel}
\renewcommand{\familydefault}{\rmdefault} %sf sans serif; rm roman
\renewcommand{\baselinestretch}{1.5}
\title{testing}
\author{Me Myself}
\date{\today}
\begin{document}
\chapter{Whatever}
this should show Greek: \bcode{*)/ANDRA MOI e)/nnepe}
and this should also show Greek: \begin{betacode}
*)/ANDRA MOI E)/NNEPE, *MOU=SA, POLU/TROPON, O(\S MA/LA POLLA\
PLA/GXQH, E)PEI\ *TROI/HS I(ERO\N PTOLI/EQRON E)/PERSE:
\end{betacode}

To be continued \dots
\end{document}
```

---

### Post by yanv on 2010-04-24
I tested your code with the latest version of the plugin, and it works for me. Do you still have problems ?

---

### Post by VCoolio on 2010-04-24
> **yanv said:**
> I tested your code with the latest version of the plugin, and it works for me. Do you still have problems ?

Thanks for your concern; I recently moved to archlinux and also I changed to emacs before that because of the 100% cpu issue with gedit. But on arch all is fine with gedit and Greek in the preview. 
Howto for arch, in case a desperate soul stumbles upon this: install gedit, install gedit-latex-plugin from aur (the one that comes builtin with gedit doesn't have the preview); for the above snippet also install texlive-langgreek and ucs (to be found on ctan or using tllocalmgr).

---

