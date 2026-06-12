---
title: "Touch - terminal command - for multiple files"
date: 2012-09-14
forum: General Help
---

### Post by KarenAK on 2012-09-14
Hi,
I wish to create empty  .txt files from a list of 150 file names that I have listed in Libre Calc. 

Read about the Touch command and that one can use it to create multiple files in one go.

Tested this and it worked ok with Test1.txt Test2.txt etc.

Problem is: Those file names are made up of several words each and some even containing special characters like ' or - or & etc.

Could someone help me with the syntax needed for this ? 
Is it at all possible ?  I do NOT want to replace the spaces with _ !
Is there a limit to the number of files that can be created at one time ?


OR: is there some other, easier way to create these files ?

Any help is much appreciated.
Thanks in advance :-)



.

---

### Post by steeldriver on 2012-09-14
if you can export the list from Calc as a text file (ideally one filename per line, i.e. making the names "newline separated") then something like

```
while read -r filename; do touch "$filename".txt; done < input.txt
```should do it (I think) provided the filenames themselves don't have newline characters in - if they do then it gets a bit more complicated

---

### Post by KarenAK on 2012-09-14
This worked like a charm !

THANK YOU :-)

---

