---
title: "substract one file from another"
date: 2011-02-25
forum: General Help
---

### Post by trojanworrier on 2011-02-25
Hi,

how do i substract one file from another. i.e. file A is super set of file B.
file A:
abc
def
ghi

file B:
abc
def

result of substracting file B from file A would be:
ghi


please advise how to do this...

---

### Post by hawkmage on 2011-02-25
Try this:
```
hawkmage@vaio:~$ cat FileA
abc
def
ghi
hawkmage@vaio:~$ cat FileB
abc
def
hawkmage@vaio:~$ grep -vFf FileB FileA
ghi
hawkmage@vaio:~$ 
```

This uses grep the 'f' makes grep use the content of FileB for the match strings.  The 'v' tells grep to list lines that do not match the match strings.  And the 'F' tells grep to not treat the match strings as a regular expression.  

If the files are large it may take a bit of memory to run.

---

### Post by rubylaser on 2011-02-25
Here's another solution, with one more step, but should be faster on big data sets...
```
admins-MacBook-Pro ~ $ cat FileA
abc
def
ghi
admins-MacBook-Pro ~ $ cat FileB
abc
def
admins-MacBook-Proo ~ $ cat FileA FileB > test
admins-MacBook-Proo ~ $ cat test
abc
def
ghi
abc
def
admins-MacBook-Proo ~ $ cat test | sort | uniq -u
ghi

```

Basically, you cat the two files together into a temporary file (test in this case), sort it, and then only return the uniq lines.  Or, you could write that output to a final file by adding 
```
> final.txt
```
to the end.

---

