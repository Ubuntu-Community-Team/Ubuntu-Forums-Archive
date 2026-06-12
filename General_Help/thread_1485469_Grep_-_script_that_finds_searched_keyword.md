---
title: "Grep - script that finds searched keyword"
date: 2010-05-16
forum: General Help
---

### Post by gin8u on 2010-05-16
Before i start, I am new to Unix/grep.

I need to the following:

> I need to write a script that can search up to 3 parameters and find all files containing those words. then display them and the amount of hits it got.

if the first parameter exists, then we can assume we are looking for the word supplied

if the second parameter exists, then we are looking for files with both keywords

if third parameter exists test the second parameter for the values ('and', 'or', '-v') and search accordingly. These are the only values accepted as the the second one when 3 parameters are present.

lastly, if there are zero or more than three parameters echo as an error and when 3 parameters have been entered we echo an error when the second parameter is not one of the following: 'and', 'or', '-v' 



I know to find 1 parameter it goes something like this:

>   grep -Rl "Keyword" * | wc -l

---

### Post by mike2357 on 2010-05-16
egrep will search for more than one parameter, but with the logic you want, I think you will have to use a combination of grep/egrep and UNIX shell scripting language, which contains if/then/else logic.  It can also count the number of parameters using "$#" which is a built-in shell variable.

---

