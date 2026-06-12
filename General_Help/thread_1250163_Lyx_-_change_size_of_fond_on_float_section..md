---
title: "Lyx - change size of fond on float section."
date: 2009-08-26
forum: General Help
---

### Post by theDaveTheRave on 2009-08-26
Dear all.

I'm using lyx (not for the first time) and starting to like it more (for the first time).

I have a query however.

I am installing a jpg file, and editing the "caption" that goes with the included file.

I can highligh the text that I would like to have appear in a smaller font (in this instance the text saying 

> LPA-induced
centrosome reorientation in serum starved fibroblasts. Centrosomes
are shown in yellow, microtubules in green and nuclei in blue (Gomes
et al. 2005).

but lyx will automatically put a legend of "figure #:" before it.

I would like to be able to at least also change the size of this text, but whenever I do I start to get errors when I generate the DVI or PDF output saying that the page could not be rendered.

here is the original code for a sample \float section....


```

\begin{figure}[h]
\noindent \begin{centering}
\includegraphics[scale=0.8]{Images/CentrosomeReorientation}
\par\end{centering}

\caption{\textendash{}\label{fig:=002013-LPA-induced-centrosome} LPA-induced
centrosome reorientation in serum starved fibroblasts. Centrosomes
are shown in yellow, microtubules in green and nuclei in blue (Gomes
et al. 2005).}



\end{figure}

```

if I insert the true latex code into the document where should I put it?

I am quite happy with putting notes onto the document then copy / pasting the full page code into a text editor and running latex on it with the correct stuff in the correct place, but I don't know if what I want to do will even work.

can I get this to work by using
\begin{figure][smaller]
or something similar??

there seems to be not option for changing the size of the legend? I can remove it, but then the referencing value is not correct (I have a lot of diagrams and have 2 in quick succesion, and so the get given the same reference value (ie figure SectionVal.SubsectionVal.SubSubectionVal) which is not only wrong and annoying it is messy!

Better still is if there is a package I can include to change the numbering or drop numbering all together?

David

---

