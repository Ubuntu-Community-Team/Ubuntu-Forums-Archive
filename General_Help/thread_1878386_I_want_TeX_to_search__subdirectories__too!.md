---
title: "I want TeX to search  subdirectories  too!"
date: 2011-11-09
forum: General Help
---

### Post by Randy Schilling on 2011-11-09
I've installed TeXLive under U11.10.  As part of the installation, you have to define
an environment variable called TEXINPUTS in the file ~/.profile; this variable lists
directories for TeX to search for your TeX macro files  \input in your primary TeX file.  
My entry in .profile is this:

export TEXINPUTS=.:/media/8A467EB6467EA29D/Documents\ and\ Settings/Randy/texmf/tex/plain/generic,

Is it possible to tell TeX (or Linux) to search all subdirectories of this directory?
If so, I could avoid a list involving five or six more directories, each listing longer than the above listing.

How might I define a variable whose value is
/media/8A467EB6467EA29D/Documents\ and\ Settings/Randy/texmf/tex/plain/generic,
and then use that variable to define TEXINPUTS?

Many thanks and regards - Randy

---

