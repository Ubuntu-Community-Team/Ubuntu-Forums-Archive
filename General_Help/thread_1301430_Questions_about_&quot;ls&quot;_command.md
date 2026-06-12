---
title: "Questions about &quot;ls&quot; command"
date: 2009-10-26
forum: General Help
---

### Post by rob86 on 2009-10-26
I'm having some problems with the ls command.

I thought the ls command used to show multiple columns of file names, but now it just lists single column, one file per line. (ls -1 style). 

I looked through the help, but I couldn't find the flag to make it go back into columns.

Second question,  according to the manual for ls, it looks like it says ls -d should list directories only. When I do this, it just echos a blank line? Am I doing something wrong, or did i misunderstand the purpose of ls -d ?

---

### Post by undecim on 2009-10-26
You probably have file names in the directory you are listing that are too long for multiple columns.

As for the -d, i don't know... never did understand myself

---

### Post by rob86 on 2009-10-26
You know, I never noticed that. When I maximize the terminal window it displays columns. Thanks.

Still wish I knew how to list directories though, if -d doesn't work, is there another command?

---

### Post by undecim on 2009-10-26
try```
find ./ -type d
```
If you use the command line a lot, it is definitely worth you time to mead the find manual

---

### Post by rob86 on 2009-10-26
I found another way to do it.

ls -d */

That seems to be the way to use ls -d and you can add other flags to it like -l also you can substitute * for a name or partial name.

---

