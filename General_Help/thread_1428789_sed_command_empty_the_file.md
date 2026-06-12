---
title: "sed command empty the file"
date: 2010-03-13
forum: General Help
---

### Post by marquinos on 2010-03-13
Hi!
I have this file: 1.txt, with this contents:
```
test
mycomputer
```I just try change the string "mycomp*" by "othercomputer":
```
sed 's/mycomp.*$/othercomputer/' 1.txt > 1.txt
```but sed command empty the file.

What is wrong, please?
Thanks very much! ;)


marcos@marcos-desktop:~/Escritoriu$ cat 1.txt 
test
mycomputer
marcos@marcos-desktop:~/Escritoriu$ sed 's/mycomp.*$/othercomputer/' 1.txt > 1.txt
marcos@marcos-desktop:~/Escritoriu$ cat 1.txt 
marcos@marcos-desktop:~/Escritoriu$

---

### Post by gmargo on 2010-03-13
You are trying to use the same file for both input and output.  The output portion ("> 1.txt") is processed first, by the shell.  The shell opens 1.txt for writing and truncates it.  Then the shell starts your sed process (attaching the open-for-writing 1.txt to sed's standard output), and sed reads from the just-truncated 1.txt file.  Try using a different filename for the output.

---

### Post by marquinos on 2010-03-13
I forget "-i" parameter :$
sed -i 's/mycomp.*$/othercomputer/' 1.txt
This question is answered ;)
Thanks!

---

