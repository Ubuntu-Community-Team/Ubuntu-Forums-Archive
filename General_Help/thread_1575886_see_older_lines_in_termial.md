---
title: "see older lines in termial"
date: 2010-09-16
forum: General Help
---

### Post by labibah on 2010-09-16
I am trying to install some piece of  software on my machine that I need for my research. The installation instruction says I need to issue a "make" command in the main directory and that should do the trick. But it looks like there are some issues with this. 
The problem is that I cannot even see the earlier error messages. The terminal only shows the last ones but when I try to see where did the problem started I can only go back to a certain number of lines. 
I tried also to pipe the output of the make command into a text file but it only shows me the beginning and does not have the rest of the stuff ( is this normal for vi?)
What should I do to go back and see more lines in the terminal?

---

### Post by philinux on 2010-09-16
> **labibah said:**
> I am trying to install some piece of  software on my machine that I need for my research. The installation instruction says I need to issue a "make" command in the main directory and that should do the trick. But it looks like there are some issues with this. 
The problem is that I cannot even see the earlier error messages. The terminal only shows the last ones but when I try to see where did the problem started I can only go back to a certain number of lines. 
I tried also to pipe the output of the make command into a text file but it only shows me the beginning and does not have the rest of the stuff ( is this normal for vi?)
What should I do to go back and see more lines in the terminal?

Edit>prefs>scrolling tick unlimited.

---

### Post by labibah on 2010-09-16
Thanks!

---

### Post by gmargo on 2010-09-16
> **labibah said:**
> 
I tried also to pipe the output of the make command into a text file but it only shows me the beginning and does not have the rest of the stuff ( is this normal for vi?)


You must not have redirected the output or errors correctly.  A basic redirection to capture everything in a file would be:
```

make > Make.out 2>&1

```Or you can watch it at the same time it goes to a file with:
```

make 2>&1 | tee Make.out

```Here's a shell function that I use all the time for compiling. Typing "makeb" starts make and captures all output in a file named "Make.out", and runs the make in the background at a low priority.  You can do a "tail -f Make.out" to watch the progress.
```

makeb()
{
    nice make "$@" > Make.out 2>&1 &
}

```

---

### Post by labibah on 2010-09-16
cool!
I'll try that.

---

