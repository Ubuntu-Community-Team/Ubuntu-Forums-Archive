---
title: "How to update pdflatex in Ubuntu 8"
date: 2012-05-20
forum: General Help
---

### Post by peterballard on 2012-05-20
I use Ubuntu 8 and it included pdflatex, a program which turns my latex source into a pdf document. But when I run Synaptic Package manager, it's not there! (To be precise, there is nothing in between "pdfjam" and "pdftk" in the alphabetical list). So how can I update pdflatex? Does it actually come with a different package? (Actually in this implementation /usr/bin/pdflatex is just a link to /usr/bin/pdftex, but pdftex is not in the Synaptic alphabetical list either).

If you're a latex expert (or anything more than me, a novice), what I actually want is either the latex package "xfrac" or "nicefrac" so I can display inline fractions like "1/2" more nicely. If it's just a matter of downloading one of them and putting it in the right place, that will do, at least for now.

Thanks in advance

---

### Post by CapnKirk on 2012-05-22
The short answer to your question is that pdflatex is part of TeX/LaTeX. It's not a good idea just to update pdflatex, because your entire TeX system could break. I don't have access to a Ubuntu 8 system (it's quite old), so I don't know what the packages might be. On a recent Ubuntu system the packages would be called "texlive-*". Just search for "tex" on synaptic.

HTH,

Kirk

---

### Post by peterballard on 2012-06-08
Sorry for the late reply. I solved my previous problem another way and came back to it today when I needed something else.

And the result: thank you! A texlive update was exactly what I needed.

---

### Post by CapnKirk on 2012-06-09
I'm glad you solved your problem.

If one is a heavy user of TeX, it is best, IMO, not to install a distro's texlive packages, but to install texlive directly from the tug.org package and update texlive from their own update manager. That way, you always have all of the commonly used packages and many of the less commonly used.

With hard disk space so cheap and plentiful these days, I don't see the need to split up texlive into so many packages as Ubuntu, Fedora, gentoo, et al., do.

One the other hand, if you rarely use TeX, then a minimal system makes sense.

---

