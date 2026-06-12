---
title: "Finding Info Page Packages"
date: 2010-01-26
forum: General Help
---

### Post by jlb.think on 2010-01-26
I am having trouble finding where to get info pages to install in ubuntu.  I've heard there is some sort of disagreement that caused the Debian crowd to turn to solely man pages, but the info pages are more detailed and very handy to have.

Does anybody know where I can get the info pages?

Simple install texinfo-doc-nonfree  to get many of the info pages, and for your specific program install the document such as:

[B]sudo apt-get install bash-doc
sudo apt-get install gcc-4.4-doc

[/B]Now I just wish I knew how to set it to automatically install the info documentation for every program and not jus the man pages.

---

