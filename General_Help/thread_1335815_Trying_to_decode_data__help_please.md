---
title: "Trying to decode data  help please"
date: 2009-11-23
forum: General Help
---

### Post by liglio on 2009-11-23
I`m using a terminal in UBUNTU, and a compiled source codes.
There are two of them,in the first when I start it it works and show me the decoded data from audio file,but the second one called dmsb.c 
I do this : ./dmsb -V
and get something like : waiting for data on stdin and nothing happens.it`s supposed to decoded the binary I got from the first code? can you helo me please? I open the stdout file but get nothing! and something more I dont have access to stdin-I cant open it i get this :could not open document stdin-there`s not installed viewer capable of displaying the document.HELP ME PLEASE

---

### Post by liglio on 2009-11-26
Is anybody going to help me ?

---

### Post by lisati on 2009-11-26
"stdin" usually refers to the keyboard. Does anything happen when you start the program and type something?

---

### Post by bwang on 2009-11-26
What program is it? What is it supposed to do?

---

### Post by falconindy on 2009-11-26
Sounds like you need to either pipe the file to the program or provide it as input. Something like `/path/to/audio/file | ./dmsb -V`

---

### Post by ibuclaw on 2009-11-28
> **liglio said:**
> I`m using a terminal in UBUNTU, and a compiled source codes.
There are two of them,in the first when I start it it works and show me the decoded data from audio file,but the second one called dmsb.c 
I do this : ./dmsb -V
and get something like : waiting for data on stdin and nothing happens.it`s supposed to decoded the binary I got from the first code? can you helo me please? I open the stdout file but get nothing! and something more I dont have access to stdin-I cant open it i get this :could not open document stdin-there`s not installed viewer capable of displaying the document.HELP ME PLEASE

If it's waiting for stdin, then what you do is feed the file to the program using '<'

ie:
```
./dsmb -V **< filename**
```
If the file is infact a device connected to the computer, use the appropriate /dev/special location in place of "filename".

Regards
Iain

---

