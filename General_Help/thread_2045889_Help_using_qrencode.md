---
title: "Help using qrencode"
date: 2012-08-22
forum: General Help
---

### Post by skycaptainbs on 2012-08-22
Helo everyone

im pretty new to linux and ubuntu but I managed to get everything running on a virtualbox :D 

I was able to install qrencode easily and i can generate simple codes using a text file as input.

the code is qrencode -o qrtest.png -s 6 < qr.txt

is it possible to somehow tell the terminal to do all text files in a certain folder and name the QR codes after the text file?

thanks in advance and sorry if this is the wrong place for this

et

---

### Post by Vaphell on 2012-08-22
```
for f in *.txt; do qrencode -o "${f%.txt}.png" -s 6 < "$f"; done
```

---

### Post by skycaptainbs on 2012-08-22
thank you alot.

i think I understand it.

I'll report back!

---

### Post by skycaptainbs on 2012-08-22
Yes perfect!

if you have the time.. would you explain what exactly it does?

no worries if not.

---

### Post by Vaphell on 2012-08-22
```
for f in *.txt; ... 
```
iterate all files matching <anything>.txt, store the current name in f variable...
```
... do qrencode -o "${f%.txt}.png" -s 6 < "$f"; done
```
loop body: execute qrencode and in proper places use $f (get value of f) placeholder which will substitute the name of the file.
*[COLOR="Green"]${f%.txt}[/COLOR].png* = [COLOR="Green"]get f, strip .txt from the right[/COLOR] and add .png
${f%pattern} is one of the parameter expansion features, there are more
[http://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion](http://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion)

```
for f in *.txt; do **echo** qrencode -o "${f%.txt}.png" -s 6 < "$f"; done
```
you can use echo so the whole command is printed out as seen by the shell, not executed. You will see the series of qrencode with individual file names placed in proper spots, 1 for each file.

---

### Post by skycaptainbs on 2012-08-22
wow even though its 2012 im starting to like command lines^^

---

### Post by Vaphell on 2012-08-22
because command line roxx, it's intimidating at first, but once you taste a bit of its goodness you feel empowered :) It's perfect for mundane stuff lending itself to programmatic approach, like perform some action on 1000 files... and the best thing is it's not rocket science ;)

---

