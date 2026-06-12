---
title: "how to edit new file via terminal?"
date: 2011-12-08
forum: General Help
---

### Post by lioreh on 2011-12-08
hello everybody... 
im new in this forum.. and im new with all the linux business
i try to learn basic linux commands...
i look out over the internet for guides.. i found a lot of them.. but none of them for begginers 
i already learn how to open new folder/files how to delete them and commands like that
now i want to edit the file via the terminal.. how can i do that?
i open new folder and new file "index.html" and i want to write few lines in the file..
in additon, if someone have a good guide for begginers i will be happy to get it

thanks in advance, lior.

---

### Post by Lars Noodén on 2011-12-08
You can edit with a program called nano.  That's easy to use and quite functional, but you have to watch out for the line breaks.  

Later you can learn a little vi.

---

### Post by killermist on 2011-12-08
I use:
```
nano -w newfile.htm
```
(-w is wide, or don't wrap)
When you're done, [ctrl-x] to quit.  It'll prompt if you want to save, select [y] for yes.

Others will recommend that you learn vi or emacs, both of which I never cared for.
Nano is sufficiently powerful and easy to use for me.

---

### Post by newbie-user on 2011-12-08
I think nano is the easiest editor to learn.  I do like the fact that nano has common commands listed at the bottom of the screen for reference, unlike some other editors.

---

### Post by lioreh on 2011-12-08
thank you :)

---

