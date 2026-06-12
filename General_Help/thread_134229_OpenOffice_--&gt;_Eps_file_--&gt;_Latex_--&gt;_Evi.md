---
title: "OpenOffice --&gt; Eps file --&gt; Latex --&gt; Evince; Nothing"
date: 2006-02-21
forum: General Help
---

### Post by jofre on 2006-02-21
Hi lads, 

I don't know if any of you would know about latex but here is my problem:

I did a simple diagram using openoffice2.0, and exported as a eps. I put the command to inserted in my latex file: 

\begin{figure}[!htb]
	\centering
  	\includegraphics[clip,keepaspectratio, viewport = 0 0 367 333 {plume_CM.eps}\\
	\caption{Pressure exerted by the plasma plume on the target.}
	\label{fig:plume_CM}
\end{figure}

Compile, no problems at all.

I use evince to see the DVI ouptut and.... there is no graphic!

If I try to visualice the eps image with evince, there is no lack, there is no error messages, but the page is just white. 

I donwloaded gv, and with it, I can see the eps image without problems. 


Well, just in case anybody has come across something similar before.

Thanks, Jofre.

(By the way, I have been using Xfce4.2: Try it!!! Is slightly minimilastic, but is so, so much faster!)

---

### Post by jofre on 2006-02-22
Ok, I did not manage to get the eps file displayed in the DVI file, but if I convert to DVI to PS, the image is there, so I guess this would do the job.

---

### Post by hajk on 2006-02-23
Saving your graphic in .PNG format, then using pdfLaTeX may be a simpler route, bypassing the .DVI step. 

Omitting the .EPS part of the filename in the \includegraphics{...} command is at any rate a smart thing to do, because LaTeX will automatically look for files with the added .EPS or .PDF extensions, and pdfLaTeX for files with added .PNG extension...

---

### Post by neoflight on 2006-02-23
[QUOTE=jofre]Ok, I did not manage to get the eps file displayed in the DVI file, but if I convert to DVI to PS, the image is there, so I guess this would do the job.[/QUOTE]

Hmm heard of that before. I think xdvi can let you view your .eps file. Mostly many dvi viewers just 'reserve' the space for the given boundingbox limits showing it as blank (of course depends on your code too; if you had given the option of showing only the fig details instead of the actual fig). 

You might wanna read this ... and its explained in much detail on using graphics on latex.
**[Using Imported Graphics in LaTeX2e by Keith Reckdahl]("http://www.ctan.org/tex-archive/info/epslatex.pdf")**
especially....page-14 (head-4)

---

### Post by hajk on 2006-02-23
That looks like an excellent paper, thanks for the reference. I also find "The LaTeX Graphics Companion" by Goossens, Rahtz and Mittelbach (Addison-Wesley, my copy dates from 1997) useful. ;)

---

### Post by jofre on 2006-03-15
It is slightly late to replay but anyway...

the trick to change from evince to xdvi, did the job. Now the pictures appears in the dvi viewer. Now I just need to find a way to change evince so it shows the picture, because xdvi is quite ugly!!! 

(By the way, I liked the old forum!)

Thanks, Jofre.

---

