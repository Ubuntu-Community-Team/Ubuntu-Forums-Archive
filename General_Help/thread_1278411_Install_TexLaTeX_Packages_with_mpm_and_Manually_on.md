---
title: "Install Tex/LaTeX Packages with mpm and Manually on Hardy"
date: 2009-09-29
forum: General Help
---

### Post by jrolland on 2009-09-29
OK, I have beat my head against the wall for long enough on this one; can someone please help?

I just installed Hardy on a new machine, and I am trying to run KILE to typeset my dissertation. I got the error message "File 'pictex.sty' not found. \usepackage". I found that mpm *is*, in fact, installed, so I gave the commands "sudo mpm --install=pictex" and "sudo texhash", and I appeared to have success.

However, I went to typeset again and got the same error message.

So, I deleted pictex from the \usepackage line, and got "File 'diagrams.sty' not found. \usepackage" error message. So, I downloaded diagrams.sty. NOW, I don't know into what directory to install the package.

Can some PLEASE tell me into what directory LaTeX .sty packages go under LaTeX in a default Hardy install and why mpm and texhash do not install the package correctly? I really need to get some work done on my dissertation on this new machine. And, can we make the answers for Hardy, Intrepid, Jaunty and other releases stickys so people can quickly identify this information when they need it?

Thanks in advance for any assistance you can provide.

---

### Post by diesch on 2009-09-29
See [https://help.ubuntu.com/community/LaTeX#Add on packages]("https://help.ubuntu.com/community/LaTeX#Add%20on%20packages")

---

### Post by jrolland on 2009-09-29
Thanks, but 1) This didn't work to install diagrams.sty 2) It doesn't help my install pictex.sty and 3) I'd like to know the default directory for installing .sty packages, not have another directory under my home directory.

I have to look up where the default .sty packages directory is every time I make a new machine; can we just post this information somewhere?

---

### Post by diesch on 2009-09-29
I don't know any program called mpm so I can't help you with that.

To install a LaTeX package you just put the files in ~/texmf/tex/latex/PACKAGENAME/ and call "texhash ~/texmf".

~/texmf/ is the standard path for per-user installed LaTeX packages. Use  /usr/local/share/texmf/ instead if you want to install them globally (needs root privileges).

---

### Post by jrolland on 2009-09-29
Thanks so much for replying!

/usr/local/share/texmf/ doesn't exist on my system, but /usr/local/share/ does; do I need to create texmf in the /usr/local/share/ directory?

(BTW, I'm installing the Ubuntu metapackage texlive-full in Synaptic; I am told this will cure some of my problems.)

---

### Post by diesch on 2009-09-29
Yes, just create /usr/local/share/texmf/

texlive-full should install pictex, but doesn't seem to have diagrams.sty

---

### Post by jrolland on 2009-09-29
OK, finally got it working!

Here's the deal, for posterity:

1) Use Synaptic (or your favorite apt driver) to install the metapackage texlive-full (WARINING: it may take several hours to download and install).

2) The directory for LaTeX packages is "/usr/share/texmf-texlive/tex/generic/". If you need to manually install any packages (say, diagrams.sty), just create a directory in /usr/share/texmf-texlive/tex/generic/ with the package's name (in this case, "diagrams") (you will need to sudo to do this) and then copy the package into that directory (in this case, /usr/share/texmf-texlive/tex/generic/diagrams/).

Hope this helps someone in the future (possibly me :)).

BTW, the .deb package for MikTeX Tools kept crashing (that's why mpm didn't work :P); maybe someone can make a .deb package for Ubuntu (or maybe several - one for Hardy, one for Intrepid, etc.)?

Thanks for all the help - you're a life- (or, at least, a dissertation-) saver!

---

### Post by Stefan_K on 2009-10-02
Hi,

concerning the mpm perhaps some of the information here could be additionally helpful: [The MiKTeX Package Manager on Ubuntu Linux]("http://texblog.net/latex-archive/linux/mpm-miktex-package-manager/").
With texlive-full you would install texlive-2007 completely, but updates would still be difficult. TeX Live 2008 brings a package manager for that purpose.
Even Kile can be used without the texlive-2007 packages it depends on, if you want to know how you could install Kile with TL 2008 or the upcoming TL 2009 without need to install the older texlive of the repositories, have a look here: [Kile and TeX Live 2008 on Ubuntu Linux]("http://texblog.net/latex-archive/linux/kile-texlive-2008-equivs/").

Stefan

---

