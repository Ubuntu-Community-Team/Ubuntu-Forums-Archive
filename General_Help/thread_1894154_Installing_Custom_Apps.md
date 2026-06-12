---
title: "Installing Custom Apps"
date: 2011-12-11
forum: General Help
---

### Post by Jacobm001 on 2011-12-11
Although I've played with Linux a few times before, I finally decided to switch over to Linux completely.  One thing I have not been able to figure out (google hasn't been much help), is how to add my own programs to terminal.  In Windows you just have to edit the PATH variable, and I'm assuming there's something similar within Ubuntu.  

I'm running the x64 flavor and my programs will be mostly written in a mix of Java, C++ and Python.

---

### Post by llamabr on 2011-12-11
I'm not quite sure what that means "add my own programs to terminal".

Describe the behavior you'd like to see.  What do these programs, which you've written, do?

---

### Post by Jacobm001 on 2011-12-11
In Linux you can run your own commands through terminal if you're within that applications current directory.  That's the same as within Windows.  In Windows however, it's possible to add the programs directory to the PATH variable.  Once added you can call that application just like any of the others within CMD.

To make it clearer, I would like myProgram, to run as a terminal command the same way say mkdir would.

---

### Post by llamabr on 2011-12-11
[http://askubuntu.com/questions/60218/how-to-add-a-directory-to-my-path](http://askubuntu.com/questions/60218/how-to-add-a-directory-to-my-path)

easy enough.  Yes, you just need to adjust your path.  For little scripts and things i write and use often, i keep them in ~/sh/ or ~/bin/ but you can put them anywhere, obviously.

---

