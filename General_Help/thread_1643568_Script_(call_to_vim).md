---
title: "Script (call to vim)"
date: 2010-12-12
forum: General Help
---

### Post by jymere on 2010-12-12
Hi.

I have a file called annu:

```
$cat annu
from pas: 1254 transmitted in 23 seconds
from jhd: 154 transmitted in 18 seconds
```I want to edit this file in order to obtain:

```
$cat annu
1254 / 23
154 / 18
```Besides I have to write a script.

So I wrote the script mod.sh:

```
$cat mod.sh
#!/bin/sh

vim <<EOF
r annu
%s/^[^0-9]*//
%s+trans.*in+ / +
%s/ seconds/ /
w
q
EOF
```but it is returned:

```
$ ./mod.sh 
Vim: Warning: Input is not from a terminal
Vim: Error reading input, exiting...
Vim: preserving files...
Vim: Finished.
```and my file "annu" is not modified.

We can noticed that it's a reading's error on the input.

Can I have some help ?

Thanks

---

### Post by jymere on 2010-12-12
good it's working !!

I changed 

ex <<EOF
r annu

to

ex annu <<EOF


thanks to geirha

---

### Post by m_duck on 2010-12-12
I know it's solved but you could also use an awk one-liner to achieve much the same unless I've missed something:```
awk '{print $3 " / " $6}' annu
```The downside being that if the format of the 'annu' file changed, this wouldn't work properly.

---

