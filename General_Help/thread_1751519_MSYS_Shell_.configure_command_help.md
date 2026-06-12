---
title: "MSYS Shell ./configure command help?"
date: 2011-05-06
forum: General Help
---

### Post by BlayneShultz on 2011-05-06
I'm trying to build Expat (using the build tool-chain, ./configure, make, make install). I am trying to do the command:

./configure

But every time I do so, it comes back and says "sh: ./configure: No such file or directory"

Am I doing something wrong?

Thanks for your help,

-Alex

BTW, this is my first time using Shell... still needing to get the hang of it.

---

### Post by spikoley on 2011-05-07
My guess is that you are not in the directory with the file.  When you first open the shell you default to your home directory (/home/username/).  You will need to use the *cd* command to move into the directory with the program.  If you saved it on your Desktop then you would use a command like the one below.

```
cd /Desktop/program-folder
```

The shell is case sensitive and that is why Desktop is capitalized.  Once you are in that directory you can run the commands.

Read this [page]("https://help.ubuntu.com/community/UsingTheTerminal") to get a better understanding of the shell.

---

