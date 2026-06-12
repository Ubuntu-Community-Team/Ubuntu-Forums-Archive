---
title: "Perl bad interpreter: No such file or directory"
date: 2009-11-25
forum: General Help
---

### Post by ve3dvv on 2009-11-25
Running Ubuntu 9.10 and Perl 
This is perl, v5.10.0 built for x86_64-linux-gnu-thread-multi

Error:
root@lserver:/usr/local/bin# ./bktar.pl
bash: ./bktar.pl: /usr/bin/perl^M: bad interpreter: No such file or directory
root@lserver:/usr/local/bin# 

How to make this work??

John, ve3dvv:o

---

### Post by diesch on 2009-11-25
Looks like you have Windows (CR/LF) line ends. See the package *tofrodos* for a simple way to convert them to Unix style (LF) line ends.

---

### Post by ve3dvv on 2009-11-25
Thank you Diesh, you saved my day. Also the "tofrodos" is handy.

---

