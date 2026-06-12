---
title: "diff command gives a weird/unusual output"
date: 2012-10-10
forum: General Help
---

### Post by fuzzylogic25 on 2012-10-10
Hello,

I wanted to compare two folders to see if all files copied were indeed identical and i got this weird output:


=======================================
Dave@Dave-CMP ~/test
$ diff -r /cygdrive/f/Imp/ /cygdrive/g/Imp/ > diffImp

[1]-  Done                    diff -r /cygdrive/f/Imp/ /cygdrive/g/Imp/ > diffImp
[2]+  Done                    diff -r /cygdrive/f/Imp/ /cygdrive/g/Imp/ > diffImp

=======================================

And the output file 'diffImp' was empty. But my question is, what were those two lines that came up in the terminal? Also, how come that did not get redirected to the file 'diffImp'?

---

### Post by dcstar on 2012-10-10
> **fuzzylogic25 said:**
> 
..........
But my question is, what were those two lines that came up in the terminal? Also, how come that did not get redirected to the file 'diffImp'?

Because programs output messages which are not part of the data being processed. You do not want want - or get - those messages in the output of the actual data.

If you don't want those messages at all then read the man page and use the "-q" option.

---

### Post by fuzzylogic25 on 2012-10-10
THanks for that, that makes perfect sense!

But do you know what they mean? Does it imply that the two folders were infact identical?

---

### Post by MG&amp;TL on 2012-10-10
> **fuzzylogic25 said:**
> THanks for that, that makes perfect sense!

But do you know what they mean? Does it imply that the two folders were infact identical?

If the file is empty, then yes. :)

---

