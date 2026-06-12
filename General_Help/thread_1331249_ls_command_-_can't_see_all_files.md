---
title: "ls command - can't see all files"
date: 2009-11-19
forum: General Help
---

### Post by bloodorange on 2009-11-19
Could someone please help me out with the ls command?  If I use it in/on a directory containing lots of files and folders, I find that they run off the screen and I can't see the ones at the top.  This isn't too much of a problem if I'm using a windowed terminal because I can use my mouse to slide up and down the window.  I can't do that in a full-screen terminal, though.

In MS-DOS, you can add a switch to the dir command that will pause the listing as it fills the screen, then you press a key and the next load of files is revealed.  Is there something similar in the Linux command line?  I keep looking in the ls man, but just can't find anything to do the job.  Perhaps I just can't see for looking!

Thanks

---

### Post by emigrant on 2009-11-19
you can give:

```
ls -l <dirctory> | less
```
use the space bar to navigate downwords.

or direct the output to a text file (to the desktop here):


```
ls -l <dirctory> > ~/Desktop/output.txt
```

---

### Post by Sin@Sin-Sacrifice on 2009-11-19
Make sure to use the -a option if you want to show hidden stuff too.

---

### Post by bloodorange on 2009-11-19
Thanks, emigrant, I'll give that a go.  Thanks for your reply, too, Sin.

---

### Post by emigrant on 2009-11-19
forgot to say,
when you give | less to come back to the terminal press q

---

### Post by bloodorange on 2009-11-19
> **emigrant said:**
> forgot to say,
when you give | less to come back to the terminal press q

Thanks again, emigrant.

---

### Post by justleen on 2009-11-19
you can also "page up" with SHIFT+PGUP  in a normal terminal..

---

### Post by bloodorange on 2009-11-19
Thanks, justleen, I didn't know that either.  That's even easier.

Cheers

---

### Post by sandy8925 on 2009-11-19
There's a more command too just like in Windows. Didn't you try that ?

---

### Post by Bjalf on 2009-11-19
> **sandy8925 said:**
> There's a more command too just like in Windows. Didn't you try that ?
less is more

:D

---

### Post by bloodorange on 2009-11-19
> **sandy8925 said:**
> There's a more command too just like in Windows. Didn't you try that ?

What is the command?

---

### Post by whitethorn on 2009-11-19
> **bloodorange said:**
> What is the command?

Hey, the command is more

as in

```
ls -al | more 
```

the " | " is called a pipe.  It takes the output from the command before it and inputs it to the command afterwards.  So in this case we take the output from ls and give it to the program "less" or "more" depending on which one you use.

---

### Post by bloodorange on 2009-11-19
Thanks very much for your prompt help everyone!

Kind regards

---

