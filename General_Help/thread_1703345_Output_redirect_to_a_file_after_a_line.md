---
title: "Output redirect to a file after a line"
date: 2011-03-09
forum: General Help
---

### Post by al_mic on 2011-03-09
Hi,

I am searching how to do this and did not found yet.

I want to redirect the output of a command to a file, but not at the end of the file, but after a line.
Do you know how can I do it?

Something like:

cat file_a | grep some_text >> resulting_file 

# in this file I need to place the output from grep, but not at the bottom of resulting_file, like it would normally  happen, but after line .. 3 , for example

Then, if file_a is:

abc x
some_text q
zxc w

and resulting_file is:

1
2
3
4
5

I want resulting_file to become:

1
2
3
some_text q
4
5


Thanks!

---

### Post by rnerwein on 2011-03-09
hi
i think you have to look at "nawk".  count the line and print.
ciao

---

### Post by al_mic on 2011-03-09
I will.

Thanks!

---

