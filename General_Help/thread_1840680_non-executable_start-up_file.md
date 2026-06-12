---
title: "non-executable start-up file"
date: 2011-09-08
forum: General Help
---

### Post by matthew2 on 2011-09-08
:guitar:trying to access MacGamut (solfege software for my music class). Can't run with wine. Receiving file not executable message. Tried changing permissions with chmod but didn't work. Used both number (1) and letter (x). 
General Syntax:
$ chmod 1/x filename
Beyond what I've done here I am at a total loss. Could really use some guidance, please. 
Thanks
Also, file type .mgs

---

### Post by Beacon11 on 2011-09-08
chmod 1 only gives execution permissions to "other" users (other than the owner and group). Try making it executable for all users (chmod a+x), or optionally turn all the bits on (chmod 777).

---

### Post by .... on 2011-09-08
What file are you trying to run? It needs to be the MacGamut executable and you need to run it with wine (because it should be a Windows executable). Do a file command on the file you're trying to execute:
```
file </path/to/file>
```

---

