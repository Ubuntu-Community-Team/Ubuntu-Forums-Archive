---
title: "Error installing GNU Octave from source"
date: 2011-04-23
forum: General Help
---

### Post by Chethan S on 2011-04-23
I was trying to install GNU Octave 3.4.0 from source. I ran ```
./configure
``` (without any options) without any errors. In the process when I ran ```
make
``` I encountered following errors:

make[3]: Entering directory `/home/chethan/Applications/octave-3.4.0/scripts' make[3]: `gethelp' is up to date. make[3]: Leaving directory `/home/chethan/Applications/octave-3.4.0/scripts' if [ "x." != "x." ] && [ -f ./DOCSTRINGS ] && [ ! -f DOCSTRINGS ]; then \         cp ./DOCSTRINGS DOCSTRINGS; \         touch -r ./DOCSTRINGS DOCSTRINGS; \     fi creating .DOCSTRINGS from .m script files ../move-if-change .DOCSTRINGS DOCSTRINGS DOCSTRINGS is unchanged touch .DOCSTRINGS make[2]: Leaving directory `/home/chethan/Applications/octave-3.4.0/scripts' Making all in doc make[2]: Entering directory `/home/chethan/Applications/octave-3.4.0/doc' Making all in faq make[3]: Entering directory `/home/chethan/Applications/octave-3.4.0/doc/faq' TEXINPUTS="./..:$TEXINPUTS" \     MAKEINFO='/bin/sh /home/chethan/Applications/octave-3.4.0/build-aux/missing --run makeinfo   -I .' \     texi2dvi OctaveFAQ.texi egrep: Invalid range end make[3]: *** [OctaveFAQ.dvi] Error 1 make[3]: Leaving directory `/home/chethan/Applications/octave-3.4.0/doc/faq' make[2]: *** [all-recursive] Error 1 make[2]: Leaving directory `/home/chethan/Applications/octave-3.4.0/doc' make[1]: *** [all-recursive] Error 1 make[1]: Leaving directory `/home/chethan/Applications/octave-3.4.0' make: *** [all] Error 2 chethan@chethan-desktop:~/Applications/octave-3.4.0$ 

I am not able make out what the error is and how to rectify it!

---

