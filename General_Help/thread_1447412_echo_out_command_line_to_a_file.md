---
title: "echo out command line to a file"
date: 2010-04-05
forum: General Help
---

### Post by johnathanamber on 2010-04-05
Hello everyone!

How can you echo out the command line results of a command to a file?

Thank you and God bless,
Johnathan

---

### Post by NoaHall on 2010-04-05
Using the ">>" will write to the end of a file. Using ">" will replace all text in the file.

So, say the command was 
```
ls -al
```
I'd do
```
ls -al >> txt.txt
```

---

### Post by johnathanamber on 2010-04-05
AH, I am familiar with that... wasn't sure it if worked in linux as it did with the Windows CL.

Thanks a ton!

BTW, hope you had a great Easter weekend!

---

