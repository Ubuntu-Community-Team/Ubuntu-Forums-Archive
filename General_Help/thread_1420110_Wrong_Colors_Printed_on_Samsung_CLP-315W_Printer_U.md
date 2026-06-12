---
title: "Wrong Colors Printed on Samsung CLP-315W Printer Under Karmic Koala"
date: 2010-03-02
forum: General Help
---

### Post by karat on 2010-03-02
I just set up a Samsung CLP-315W printer on my Karmic Koala Ubuntu system.

I can find the printer, but the printer colors are swapped in color mode.

The user manual claims this is a common Linux problem:

"Some color images come out in unexpected color"
"This is a known bug in Ghostscript (until GNU Ghostscript version 7.xx) when the base color space of the document in indexed RGB color space and it is converted through CIE color space.  Because Postscript uses CIE color space for Color Matching System, you should upgrade Ghostscript on your system to at least GNU Ghostscript version 8.xx or later.  You can find recent Ghostscript versions at www.ghostscript.com."

I am running Ghostscript 8.7x, but I still have this problem.

1) Does anyone recognize this as a generally known problem?  Searching didn't turn up this bug in a cursory search.

2) Was this fixed in Ghostscript 8.7x?

3) I confess that I do not understand the current hardware paradigm between free and vendor drivers.  As such, I've had a hard time figuring out what driver my system is using and trying to figure out if I could replace it with a different one, if it turns out to be a driver problem.  How can I do this?

---

