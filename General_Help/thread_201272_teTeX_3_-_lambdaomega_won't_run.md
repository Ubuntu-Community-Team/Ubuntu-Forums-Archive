---
title: "teTeX 3 - lambda/omega won't run"
date: 2006-06-21
forum: General Help
---

### Post by amerikkanu on 2006-06-21
hey, i'm new to both TeX and linux, and lambda is now giving me problems beyond my limited know-how.  i'm not sure whether my recent attempts to fix hyphenation or a recent update might have thrown my system out of whack, but i need lambda for my work, so any suggestions would be much appreciated!  i'll addend the error msg. i get when i try to run it.  thanks in advance, guys.

************************

This is Omega, Version 3.141592-1.23.2.3 (Web2C 7.5.4)
Copyright (c) 1994--2000 John Plaice and Yannis Haralambous
kpathsea: Running mktexfmt lambda.fmt
mktexfmt: running `omega -ini   -jobname=lambda -progname=lambda lambda.ini' ...! omega.pool doesn't match; otangle me again (or fix the path).
Error: `omega -ini  -jobname=lambda -progname=lambda lambda.ini' failed

###############################################################################
mktexfmt: Error! Not all formats have been built successfully.
Visit the log files in directory
  /home/guy/.texmf-var/web2c
for details.
###############################################################################

This is a summary of all `failed' messages and warnings:
`omega -ini  -jobname=lambda -progname=lambda lambda.ini' failed
warning: kpathsea: mktexpk output `! omega.pool doesn't match; otangle me again (or fix the path).' instead of a filename.
I can't find the format file `lambda.fmt'!

---

### Post by amerikkanu on 2006-06-21
Thanks for the views; the problem (whatever it was) is now solved.  By simply removing and reinstalling the necessary LaTeX programs and their dependencies, lambda/omega work fine now - as does hyphenation!

---

