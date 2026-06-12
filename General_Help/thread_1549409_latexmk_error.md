---
title: "latexmk error"
date: 2010-08-09
forum: General Help
---

### Post by Raq0 on 2010-08-09
Hey all, this is my first time posting on this forum but I know this forum always comes up with great answers and fixes to various issues. I hope someone can help me out with an error latexmk is giving me.

I use texmaker as an editor with latexmk along side it. latexmk never gave me a problem until I installed lucid lynx (though I'm not sure that has anything to do with the issue).

I input this into the terminal:

$ latexmk -pvc -pdf filename.tex 

and this is the error:

=== Watching for updated files. Use ctrl/C to stop ...
Error: PDF file is damaged - attempting to reconstruct xref table...
Error: Couldn't find trailer dictionary
Error: Couldn't read xref table

for another file (my resume) I'm using res.cls and the resume class but I get a different error:

No auxiliary output files.

) (./RMurrayResume.aux) (/usr/share/texmf-texlive/tex/latex/base/omscmr.fd)
[1{/var/lib/texmf/fonts/map/pdftex/updmap/pdftex.map}pdflatex: RMurrayResume: Operation not supported
Latexmk: restoring last RMurrayResume.aux file

Thanks in advance for your help!
Raq

---

