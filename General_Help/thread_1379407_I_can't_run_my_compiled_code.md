---
title: "I can't run my compiled code"
date: 2010-01-12
forum: General Help
---

### Post by ElHermit on 2010-01-12
Hello, I am running Ubuntu 9.10.  If I compile a 'hello world' C file using the terminal, something like: 

gcc hello.c -o hello

the compile seems to work fine, and the executable file 'hello' appears in the directory.  

However, when I try to run 'hello' from the terminal, I get something like the following:

No command 'hello' found, did you mean: .......

If I run dir, though, I can see 'hello' is there.  I also can't run code I compiled when I was running 9.04.  The OS again can't seem to find the executable file.

Everything worked fine with version 9.04.  I could compile and run without any problems.  Is there some setting I have to change to allow the OS to run my code?

Thanks.

---

### Post by ElHermit on 2010-01-12
Oops -- if figured it out.  I need to type ./hello to run the program.

---

### Post by Tyke91 on 2010-01-12
or put it in the correct file.

ubuntu will check /bin /usr/bin /sbin (for admins) and /usr/sbin (for admins) when you type a command. if you wrote a program yourself and like it alot, you could throw it into /usr/bin to run it.

./hello just means the path of the working directory + hello... if it were in /home/userjoe/workspace then you could also type /home/userjoe/workspace/hello

---

### Post by patchwork on 2010-01-12
It's probably a good idea to include the -Wall argument when compiling, as well. This will output most common compiler errors to the terminal.  My understanding is that without this argument, most compiler errors won't show?

---

