---
title: "dmtxwrite: help with the command"
date: 2012-09-18
forum: General Help
---

### Post by skycaptainbs on 2012-09-18
Hi im pretty new to this, can someone help me with my Ubuntu problem?

im trying to create a Datamatrix code using dmtxwrite but it doesnt work at all.

i got qrencode to work and create a code out of text with this: qrencode -o qrtest.png -s 6 < qrtest.txt

if i try the similar line with dmtxwrite I get: 
Usage: dmtx (OPTION) ... (FILE)

dmtxwrite and its usage is here: [http://manpages.ubuntu.com/manpages/karmic/man1/dmtxwrite.1.html](http://manpages.ubuntu.com/manpages/karmic/man1/dmtxwrite.1.html)

I know im a newb but could someone explain why I cant get it to work?

(Edit)
alright. got it to work with this:

dmtxwrite -e c -o Part1.png Part1.txt


thanks anyways.

---

