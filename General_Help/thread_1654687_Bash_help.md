---
title: "Bash help"
date: 2010-12-28
forum: General Help
---

### Post by fistikuffs on 2010-12-28
Howdy, I'm trying to do a bit of server admin but my poor bash skills are letting me down. I have a folder containing folders named after months of the year, jan, feb etc and in each folder is a txt file foo.txt. I need to rename each txt file to the same name as the folder it is in eg jan/jan.txt. Not sure where to start. Should i use mv or rename?

---

### Post by kkaldroma on 2010-12-28
#! /bin/bash
      I would read all folder names into an "array"
FILES=($(ls  <location of folder holding month folders>)
      Run a loop with the mv command indexing the FILES "array"
LEN= ${#FILES[@]} //finds number of fines in the array
x=0 // counter
while [$LEN -ge x]
do
FILE=$(echo ${FILES[X]} | cut -d '/' -f2) //cuts out the / in the file name. you may need to is -f3 or -4 depending on how many folders deep yours is.

mv ${FILES[X]}/foo.txt ${FILES[X]}/$FILE.txt 

let X++
done

     Play around with this, I have no way of testing.

---

### Post by fistikuffs on 2010-12-28
> **kkaldroma said:**
> #! /bin/bash
      I would read all folder names into an "array"
FILES=($(ls  <location of folder holding month folders>)
      Run a loop with the mv command indexing the FILES "array"
LEN= ${#FILES[@]} //finds number of fines in the array
x=0 // counter
while [$LEN -ge x]
do
FILE=$(echo ${FILES[X]} | cut -d '/' -f2) //cuts out the / in the file name. you may need to is -f3 or -4 depending on how many folders deep yours is.

mv ${FILES[X]}/foo.txt ${FILES[X]}/$FILE.txt 

let X++
done

     Play around with this, I have no way of testing.

Cheers mate something to get started with:p

---

