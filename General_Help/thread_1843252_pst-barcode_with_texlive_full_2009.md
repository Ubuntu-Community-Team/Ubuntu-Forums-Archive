---
title: "pst-barcode with texlive full 2009"
date: 2011-09-13
forum: General Help
---

### Post by rdst on 2011-09-13
hi all,

I tried to make an article which contains a QR code using these:

```

\documentclass[letterpaper]{article}
\usepackage{pstricks}
\usepackage{pst-barcode}
\begin{document}
\begin{pspicture}(3.5,1.2in)
\psbarcode{W0001}{guardwhitespace}{code39}
\end{pspicture}
\end{document} 

```and save in qrcode.tex file

I'm using Ubuntu 10.10. I've installed texlive-full. I compile this .tex file with the command:

```

latex qrcode.tex

```There's a .dvi file generated successfully but nothing in this file. The file is blank !!!
Please tell me, anything wrong !!

Thank you !

PS: I also attach my .tex file along with the .log file.

---

### Post by wt8008 on 2011-09-13
Please continue and generate the PS and PDF file. PS tricks  generates postscript code, so you require one more processing stage.

---

