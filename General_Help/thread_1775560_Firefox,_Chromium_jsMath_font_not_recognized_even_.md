---
title: "Firefox, Chromium: jsMath font not recognized even though it is correctly installed"
date: 2011-06-04
forum: General Help
---

### Post by meladoro on 2011-06-04
Hi all, I'm having some trouble with jsMath fonts in Firefox and Chromium that I hope somebody can help me with.

[Note: I've posted this as a bug at [https://bugs.launchpad.net/ubuntu/+source/ttf-jsmath/+bug/792980](https://bugs.launchpad.net/ubuntu/+source/ttf-jsmath/+bug/792980) so please go there if you want full verbosity. The gist is below.]

The issue:

After installing ttf-jsmath (0.090709+0-1), pages featuring jsMath TrueType fonts fail to recognize and use the jsMath-cmmib10 font even though it is correctly installed via the ttf-jsmath package.

In Firefox 4.0.1, a jsMath error message is displayed, quoted here in full:

"Extra TeX fonts not found: jsMath-cmmib10
Using image fonts instead. This may be slow and might not print well.
Use the jsMath control panel to get additional information."

In Chromium 11.0.696.71 (86024) no jsMath error message is displayed but, as in Firefox, math using the jsMath-cmmib10 font is rendered using images while everything else is properly displayed using the TrueType fonts.

Before installing the package, the same page displayed the same kind of error message in Firefox, but referencing many jsMath fonts rather than just jsMath-cmmib10. Installing the package made the error go away for all fonts except for jsMath-cmmib10, even though the relevant .ttf file is contained in the ttf-jsmath package and gets installed properly along with every other font.

I have tried replacing jsMath-cmmib10 with the version located at [http://www.math.union.edu/~dpvc/jsMath/download/extra-fonts/welcome.html:](http://www.math.union.edu/~dpvc/jsMath/download/extra-fonts/welcome.html:) no results. The behavior remains unchanged.

One of the pages I used to test this is: [http://planetmath.org/encyclopedia/LinearOperator.html](http://planetmath.org/encyclopedia/LinearOperator.html)

I'm using Ubuntu 11.04 (Natty) and ttf-jsmath 0.090709+0-1.

Thank you very much. Any help is very much appreciated.
_______
meladoro

---

### Post by 6eKkhfa on 2011-06-24
I have this same problem. Unfortunately, I can offer no solution!

---

