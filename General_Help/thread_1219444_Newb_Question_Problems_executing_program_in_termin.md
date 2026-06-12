---
title: "Newb Question: Problems executing program in terminal"
date: 2009-07-21
forum: General Help
---

### Post by kgeary on 2009-07-21
I just started running Ubuntu yesterday so please be patient with me...

I managed to build a small hello world style application using GCC using the command

*gcc test.c -o testprogram*

However when I try to run the output from a terminal I get the error message:

*testprogram: command not found*

If I instead double click this file from a GUI based file explorer window (not sure the linux term yet) the program executes properly.   Why can't I run this from the terminal though?

Thanks in advance

---

### Post by devildoc5 on 2009-07-21
well to make a long story short.....are you sure that you are in the proper folder when trying to execute the command?

---

### Post by Vaphell on 2009-07-21
because you have to run it by ./testprogram from the dir (dot=current dir) with it or by full path in general ( /full/path/to/program/testprogram)

testprogram would work if it was available in any of system paths

---

### Post by kgeary on 2009-07-21
> **devildoc5 said:**
> well to make a long story short.....are you sure that you are in the proper folder when trying to execute the command?

the output from the build appears in the current directory when I do LS, so I would say yes(?).

---

### Post by ibutho on 2009-07-21
To execute the program, use the full path name e.g. /home/someuser/programs/testprogram or navigate to the directory containing the program and run "./testprogram" (without the quotes).

---

### Post by wojox on 2009-07-21
Do what vaphell just told you ./program

---

### Post by kgeary on 2009-07-21
> **wojox said:**
> Do what vaphell just told you ./program

Ah yes, that did the trick.  Thank you all much

---

### Post by lukeiamyourfather on 2009-07-21
> **Vaphell said:**
> because you have to run it by ./testprogram from the dir (dot=current dir) with it or by full path in general ( /full/path/to/program/testprogram)

testprogram would work if it was available in any of system paths

What he/she said. If the command is entered without any path it assumes to check the system path. Using "./command" it looks in the current directory for the command instead of the system path. Or using the full path works too.

Use "echo $PATH" to see what directories are already in the system path if you're curious. Cheers!

---

