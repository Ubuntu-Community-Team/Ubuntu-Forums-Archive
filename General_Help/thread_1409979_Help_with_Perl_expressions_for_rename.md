---
title: "Help with Perl expressions for rename"
date: 2010-02-18
forum: General Help
---

### Post by Kenny_Larsen on 2010-02-18
Hi All,

I seem to be fighting a losing battle to get rename to work! I have never used perl at all so am muddling my way through.

I have a folder of files, essentially labelled on_Dose1.txt, on_Dose2.txt ... on_Dose20.txt

All I want to do is change the first o to an O, remove the _, seperate the number from the Dose and add a space then the word Square after the number. I have managed by running 

```
rename 's/on/On/' *.txt
```

And Similarly to change the _ to a space, however I can't work out how to seperate the Dose fron the number, nor add the word Square in after?

Any help would be appreciated (before I attempt several hundred by hand!) :)

Kenny

---

### Post by sisco311 on 2010-02-18
Replace "Dose" with "Dose " then ".txt" with " Square.txt".

EDIT: 
All in one command:
```
rename -n 's/on_Dose([0-9]+?).txt/On Dose $1 Square.txt/' *.txt
```

[http://perldoc.perl.org/perlre.html#Regular-Expressions](http://perldoc.perl.org/perlre.html#Regular-Expressions)

---

### Post by Kenny_Larsen on 2010-02-18
Thanks! And thanks for the link!

Kenny

---

