---
title: "LaTex: beamer files no longer compile"
date: 2012-05-13
forum: General Help
---

### Post by peredur on 2012-05-13
I have a number of latex beamer files that I created about a year ago.  Having now updated to the latest versions of Ubuntu and Kile, these files no longer compile. Every \end{frame} gives the error message "unknown control sequence".

Not even the Kile beamer template compiles in its unchanged state.

Cheers


Peter

---

### Post by katu on 2012-05-23
I have the same problem. I just downloaded the examples of beamerposter and I can't compile them with kile due to this error.
I'm on Kubuntu 11.10.

Have you found a solution?

---

### Post by peredur on 2012-05-23
> **katu said:**
> I have the same problem. I just downloaded the examples of beamerposter and I can't compile them with kile due to this error.
I'm on Kubuntu 11.10.

Have you found a solution?
Not really.  I installed Kile on a different box and worked from the Beamer template - which compiled without problem.

BTW, does Kile crash on you if you close it without closing the current project?

---

### Post by katu on 2012-05-23
Hi there,
no, it doesn't crash. What version of kile and beamer are you using on the second box (the one that works)?

I have beamer oneiric 3.10-1
and kile 1:2.1.0-1ubuntu1

thanks.

---

### Post by Erik1984 on 2012-05-23
They seem unrelated but have you installed texlive-latex-extra? I needed that to include some packages I use or else I got similar errors like you only on the \end{document} in stead of frame. texlive was not included when I installed Kile.

---

### Post by peredur on 2012-05-23
> **katu said:**
> Hi there,
no, it doesn't crash. What version of kile and beamer are you using on the second box (the one that works)?

I have beamer oneiric 3.10-1
and kile 1:2.1.0-1ubuntu1

thanks.
Same versions of Kile and beamer.  Onething does occur to me.  The problems with beamer were on a 64bit installation.  The one that works is a 32bit system.

I get the crashing on both systems.

---

### Post by peredur on 2012-05-23
> **Euroman said:**
> They seem unrelated but have you installed texlive-latex-extra? I needed that to include some packages I use or else I got similar errors like you only on the \end{document} in stead of frame. texlive was not included when I installed Kile.
That's true.  One system may have that installed and the other not.  I'll check.

---

### Post by katu on 2012-05-23
> **Euroman said:**
> They seem unrelated but have you installed texlive-latex-extra? I needed that to include some packages I use or else I got similar errors like you only on the \end{document} in stead of frame. texlive was not included when I installed Kile.

Hi,
I do have it installed. I actually checked for all the latex packages beamerposter claims it needs and I can find them in my directories.

I am on a 64 bit install though. could be that. Argh. :/

---

### Post by katu on 2012-05-23
Incidentally, if I run pdflatex on the .tex example I still get the /end{frame} error, however it can somehow live with that.
I get a poster that's two pages though, so I'm not really happy with that yet.

---

### Post by katu on 2012-05-23
Ok, I seached for the actual pdflatex error and found this page:

[https://groups.google.com/forum/#!msg/beamerposter/vWI5sde-Iq0/OzqqQWEIBhIJ](https://groups.google.com/forum/#!msg/beamerposter/vWI5sde-Iq0/OzqqQWEIBhIJ)

this solves the beamerposter issue for me. I don't know if it helps on your case. Good luck.

---

