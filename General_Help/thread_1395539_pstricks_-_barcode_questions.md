---
title: "pstricks - barcode questions"
date: 2010-02-01
forum: General Help
---

### Post by OlympusRunner on 2010-02-01
Hi,

I am running Ubuntu 9.10 and

texlive-latex-base
2007.dfsg.2-4ubuntu1 (karmic)

texlive-pstricks
2007.dfsg.17-2ubuntu1 (karmic)

LaTeX works great but I am having some issues with pstricks.
My problems are specific to the pst-barcode package.

I tried doing latex -> dvips -> ps2pdf on the following file but I received an error

===============================

\documentclass{article}
\usepackage{pst-pdf,pst-barcode}
\begin{document}


\begin{pspicture}(1in,1in)
\psbarcode{http://www.dante.de}{}{qrcode}
\end{pspicture}


\end{document}

===============================

I get this error:

===============================

olympusrunner@battlemachine:~/Documents/test$ ps2pdf one.ps
Error: /undefined in qrcode
Operand stack:
   ([http://www.dante.de](http://www.dante.de))   ()
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1862   1   3   %oparray_pop   1861   1   3   %oparray_pop   1845   1   3   %oparray_pop   1739   1   3   %oparray_pop   --nostringval--   %errorexec_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--
Dictionary stack:
   --dict:1154/1684(ro)(G)--   --dict:0/20(G)--   --dict:101/200(L)--   --dict:95/300(L)--   --dict:40/200(L)--   --dict:84/200(L)--
Current allocation mode is local
Last OS error: 2
Current file position is 142590
GPL Ghostscript 8.70: Unrecoverable error, exit code 1

==============================

I found the following posting:

[http://www.tug.org/pipermail/texhax/2009-September/013160.html](http://www.tug.org/pipermail/texhax/2009-September/013160.html)

[http://www.tug.org/pipermail/texhax/2009-September/013161.html](http://www.tug.org/pipermail/texhax/2009-September/013161.html)

Are my files up to date? I used Synaptic Package Manager to install "texlive-latex-base", "texlive-pstricks", and some other LaTeX packages.

Do I just find those files listed in the other TUG forum and paste them into 
/usr/share/texmf-texlive/tex/latex/pstricks/
and its other folders?

Any help would be appreciated. I would really like to use the QR Codes in LaTeX but im a bit of a noob.

Thanks,

OR

---

