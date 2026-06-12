---
title: "Gummi LateX Compiling Error"
date: 2010-10-19
forum: General Help
---

### Post by egonskinny on 2010-10-19
When I open my tex file with Gummi it states that there is an error ("pdf could not initialize") that does not allow for it to compile. After reading the errors I can tell this is most likely due to the fact that the files I am pointing to in my tex file are not being recognized by Gummi. My first guess is that Gummi has a pointer that looks in some other area of the memory.  I am a noob and am currently unable to solve this in a sufficient amount of time. Listed below are the errors that were outputted when I opened my tex file with Gummi (where it is stated "undefined on input line 'x'" I am simply stating that some line points to an undefined file X:



Package epstopdf Warning: No graphics package `graphic{s,x}' loaded.


LaTeX Warning: Citation `X' on page 1 undefined on input line a.



[1{/var/lib/texmf/fonts/map/pdftex/updmap/pdftex.map}]




Overfull \hbox (50.31091pt too wide) in paragraph at lines 88--109
 [] 
<Model10_6_10.pdf, id=24, 794.97pt x 614.295pt> <use Model10_6_10.pdf>

LaTeX Warning: Reference `fig:Model1 Diagram' on page 5 undefined on input line
 117.

[5] [6] [7 <./Model10_6_10.pdf, page is rotated 90 degrees>]
Underfull \hbox (badness 10000) in paragraph at lines 123--125


LaTeX Warning: Reference `eq:mosquito1' on page 8 undefined on input line 126.


Overfull \hbox (27.35445pt too wide) in paragraph at lines 131--134
\OT1/cmr/m/n/10.95 ble to malaria in-fec-tion. Note that $\OML/cmm/m/it/10.95 m
[] \OT1/cmr/m/n/10.95 = \OMS/cmsy/m/n/10.95 ^^@\OML/cmm/m/it/10.95 j[] \OT1/cmr
/m/n/10.95 = \OMS/cmsy/m/n/10.95 ^^@ [] \OML/cmm/m/it/10.95 m \OMS/cmsy/m/n/10.
95 ^^@

Underfull \hbox (badness 10000) in paragraph at lines 131--134

[8]

LaTeX Warning: Citation `X' on page 1 undefined on input line b.


Overfull \hbox (1.17723pt too wide) in paragraph at lines 252--262
 [] 


Overfull \hbox (55.08757pt too wide) in paragraph at lines 270--305
 [] 
<IndiaPopFit2.pdf, id=70, 504.88625pt x 503.8825pt> <use IndiaPopFit2.pdf>

LaTeX Warning: Citation `PopData' on page 11 undefined on input line 314.


LaTeX Warning: Citation `PopData' on page 11 undefined on input line 314.

[11]

LaTeX Warning: Citation `X' on page 1 undefined on input line c.


/tmp/tmpCOtUgT.tex:345: LaTeX Error: File `IndCases2' not found.

See the LaTeX manual or LaTeX Companion for explanation.
Type  H <return>  for immediate help.
 ...                                              
                                                  
l.345 \label{fig:Cases}}
                        
/tmp/tmpCOtUgT.tex:345:  ==> Fatal error occurred, no output PDF file produced!
Transcript written on /tmp/tmpCOtUgT.log.





Please help me determine what stupid mistakes I am making. Thanks.

---

### Post by cugat on 2010-10-27
I tried Gummi, but it didn't work for me. I suggest you ditch it and get one of the other editors like TexWorks. It seems more stable.

From what you posted, it looks like you need \usepackage{graphicx} in your preamble to get rid of the first error, and your figure should appear as 
\begin{figure}
\includegraphics{figure_name.eps}
\caption{something}
\end{figure}

That should get you something you can work with.

---

