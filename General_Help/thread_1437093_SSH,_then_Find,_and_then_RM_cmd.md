---
title: "SSH, then Find, and then RM cmd"
date: 2010-03-23
forum: General Help
---

### Post by slimx3m on 2010-03-23
i need some help with a script that i've been having some difficulties within the last 3 weeks.  i've try researching everything but nothing has worked yet.  

summary:
here is what i am trying to do...... connect to my remote server from local computer, do a search for files older than 7 days, and then remove those files.

able to:
i can run my command line with no problem if i am on the remote server and from local pc if i don't use the SSH or using SSH and not the rm cmd

here are my codes with some explanation

[SIZE="3"]Code #1[/SIZE]
[LIST=1]
[*]this code works on the remote server with no problem
```
find path/to/file* -mtime +7 -exec rm {} \;
```
[*]this code works from local to remote
```
ssh fName@domain.com find path/to/file* -mtime +7
```
[*]this code FAILS from local to remote ](*,)
```
ssh fName@domain.com find path/to/file* -mtime +7 -exec rm {} \;
```
[/LIST]
[SIZE="3"]Code #2[/SIZE]
[LIST=1]
[*]this code works on the remote server with no problem
```
find path/to/file* -mtime +7 | xargs rm -f
```
[*]this code works from local to remote
```
ssh fName@domain.com find path/to/file* -mtime +7
```
[*]this code FAILS from local to remote ](*,)
```
ssh fName@domain.com find path/to/file* -mtime +7 | xargs rm -f
```
[/LIST]

Note: the codes are suppose to do the same thing, but i am trying two different type of code until i find the one that works :)

any thoughts? thnx for your help in advance.

---

### Post by rnerwein on 2010-03-23
hi
you must quote it and use following syntax:
ssh [email]fName@domain.com[/email] [COLOR=Red]"[/COLOR]find path/to/file* -mtime +7 -exec rm -f [COLOR=Red]{} \;"
[COLOR=Black]
ciao
[/COLOR][/COLOR]

---

### Post by slimx3m on 2010-03-23
thnx :D........ that definetly did the trick.

---

### Post by siogwah on 2010-03-23
you might want to try:

find . -mtime +7 -print0 | xargs -0 rm -f

as it will also handle filenames containing whitespace.
   Can be a little more efficient also.

Bob Thorson

---

