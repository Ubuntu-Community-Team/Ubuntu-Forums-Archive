---
title: "Count the number of times a certain letter has occurred in a text file"
date: 2009-07-31
forum: General Help
---

### Post by lethalfang on 2009-07-31
As the title suggests, what command(s) do I use to count the number of times the letter "A" has occurred in a text document?
Basically, I'm looking at a bunch of text files containing DNA sequences. I'd like to know how many A's, G's, T's, and C's are there.

Thanks!

---

### Post by danwood76 on 2009-07-31
Have a look into using Regex (Regular Exprisions) or maybe even Grep.
Write a simple bash script to read a file and use Regex to find letters and bash to count.

---

### Post by hamstersquasher on 2009-07-31
try this...
grep -o 'letter' filename | wc -w

grep with the o switch greps for *only* what is in quotes (which just happens to be one letter).  that output is then piped into the wordcount command which only lists the occurances of that word with the w switch.

---

### Post by lethalfang on 2009-07-31
> **hamstersquasher said:**
> try this...
grep -o 'letter' filename | wc -w

grep with the o switch greps for *only* what is in quotes (which just happens to be one letter).  that output is then piped into the wordcount command which only lists the occurances of that word with the w switch.

Thanks. That worked perfectly!
I didn't know about the -o flag for grep, and that's the key! :)

---

