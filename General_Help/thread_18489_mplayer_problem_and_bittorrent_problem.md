---
title: "mplayer problem and bittorrent problem"
date: 2005-03-07
forum: General Help
---

### Post by Kimm on 2005-03-07
ok, yesterday I installed mplayer on my system. I compiled it from source that I got from the website. mplayer runns nicely, it plays music and everything. But I cant seem to be able to run gmplayer, that is, the GUI version of it, it just says "command not found" in the console when I try it. Does anyone know what's wrong?

Also... this isnt an mplayer problem but I figured I wouldent make two separate topics. I have intalled BitTorrent... but I dont know how to use it, btdownloadgui in the console wount work 'cos it requires some wxPython library or something like that, I have had some bad luck installing library dependencies so I'm a bit carefull when it comes to that... but I'm sure there must be a command like client also??

Thank you in advance :)

---

### Post by valfader on 2005-03-07
The reason you dont have gmplayer is most probably because you did not complie with the "--enable-gui" option.

There is two command line version with bittorrent,   btdownloadcurses (best) and btdownloadheadless. But if you install the wxpython (and maybe some more) package, the gui version should work...

---

### Post by Kimm on 2005-03-07
> 
The reason you dont have gmplayer is most probably because you did not complie with the "--enable-gui" option.


yes... I supose that would explain it :P I'll recompile it then...

> 
if you install the wxpython (and maybe some more) package, the gui version should work...


ok... where can I find that package?

---

### Post by Kimm on 2005-03-07
ok... when I try to run

> 
make --enable-gui


it just says "unrecogniced flagg".
how should I run it??

---

### Post by Kimm on 2005-03-07
ok... never mind :razz: 
I went to have a look at the installation instructions (D'oh), and ofcourse I should do it in ./configure... oh well, you cant know everything :razz:

---

