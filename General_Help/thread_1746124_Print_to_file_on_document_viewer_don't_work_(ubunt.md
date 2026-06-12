---
title: "Print to file on document viewer don't work (ubuntu 11.04"
date: 2011-05-01
forum: General Help
---

### Post by gargaralarga on 2011-05-01
Hi,

Though I have to deal with a lot of new issues with respect to 11.04, I have a specific problem that I need to solve quickly. When I try to print to a pdf-file from a ps-file using Document Viewer, it appears a box that says:

"Failed to print document

Printing is not supported on this printer."

Any suggestions?

Thanks!

---

### Post by meithan on 2011-05-14
I'm having the exact same issue. This worked flawlessly on 10.10 Maverick. Anyone?

**Update**: I think I found a solution. It seems the "Print to File" options requires the cups-pdf package, which was removed from the default Maverick package set for some reason.

So the solution is to install the cups-pdf package manually. In the terminal, type:

> sudo apt-get install cups-pdf

Once installed, a new printer called "PDF" will appear in your printers list. You can use this one if you like, but the bonus is that the "Print to File" option will now work (and you'll have to option to print to SVG too).

**Update 2**: whatever I did, it's *not* working again :(

---

