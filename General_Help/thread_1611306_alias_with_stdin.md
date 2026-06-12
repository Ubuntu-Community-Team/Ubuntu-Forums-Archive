---
title: "alias with stdin"
date: 2010-11-01
forum: General Help
---

### Post by mtphr on 2010-11-01
hi everyone.

there's a software called ds9 that i want to run with certain parameters, but the problem is, it only accepts some parameters "after" the filename.

```
$ ds9 -zscale -zoom to fit myfile.fits
```

the zscale option works here but the "-zoom to fit" doesn't. (no, it's not cuz of the spaces)

instead this works,

```
$ ds9 -zscale myfile.fits -zoom to fit
```

now i want ds9 to run with "zscale" and "zoom to fit" options allways on. so i want to define an alias with the standard input in the middle somewhere.
something like this: (i know it doesn't work)

```
alias ds9='ds9 -zscale $1 -zoom to fit'
```

is there any way of doing this? thanks in advance.

---

### Post by HiImTye on 2010-11-01
[https://bbs.archlinux.org/viewtopic.php?id=61044](https://bbs.archlinux.org/viewtopic.php?id=61044)
the site in question defines a function instead of creating an alias as alias only looks for variables at the end. the alias they want to create is:
```
alias findcp="find -iname \"$1\" -exec cp '{}' $2/ \;"
```unfortunately, this cannot work due to the variables being inside. they create the following function:
```
function findcp() { find -iname "$1" -exec cp '{}' $2/ \; ;}
```so, taking your initial idea of an alias:
```
alias ds9='ds9 -zscale $1 -zoom to fit'
```we can form the following function
```
function ds9run() { ds9 zscale "$1" -zoom to fit; }
```

---

### Post by blueridgedog on 2010-11-01
An alias is not the right tool.  You need to write a bash script that takes an argument and then runs the command you want.

Such as the following saved as myscript.sh and run as follows:

myscript.sh myfile.fits

with myscript.sh looking something like:

```
#!/bin/bash
`ds9 -zscale $1 -zoom to fit`
```

---

### Post by mtphr on 2010-11-10
thanks guys!
for the record, before reading your solutions, i've found out my own bundled one. it works too and looks like this.

```
alias ds9='echo "-zoom to fit" | xargs ds9 -zscale'
```

but as u guys mentioned, maybe defining an alias isn't the best way to do this.

---

