---
title: "Sending output to a spreadsheet"
date: 2010-06-02
forum: General Help
---

### Post by KeilanS on 2010-06-02
Hey everyone,

I've got some code that I need to use to output results quite often. I'd like to write some sort of script to automate getting these results in a nice form. Basically here is what I need to do.

1. Compile program
2. Run program (outputs values a, b, and c)
3. Compile program with flag x
4. Run program (outputs values d, e, and f)
5. Compile program with flag y
6. Run program (outputs values g, h, i)

I want to do that automatically, and put those into a spreadsheet. Now I know I could use a csv file, but the problem is I need a row in the spreadsheet to have the data values in the order a,d,g,b,e,h,c,f,i (that is, not in the order I receive them in).

Is there a command that will say something like "take 'a' and put in row 2, column 3"? I'm using open office by the way.

Many thanks for any help.
-Keilan

---

### Post by Tim Sharitt on 2010-06-03
You might try ooolib for python (python-ooolib in the repos). I never got around to messing with it too much, so I can't really give any details about how to use it but it may be worth a look.

If you're more comfortable with perl,libopenoffice-oodoc-perl might be worth a look to too (I've never even toyed with this, just came across it while looking for ooolib's package name).

---

### Post by geirha on 2010-06-03
Something like this?
```
#!/bin/bash
read -r a b c < <(./prog)
read -r d e f < <(./prog)
read -r g h i < <(./prog)
echo "$a,$d,$g,$b,$e,$h,$c,$f,$i" >> file.csv

```

---

### Post by KeilanS on 2010-06-03
Geirha, that is what I was looking for. Thanks!

---

