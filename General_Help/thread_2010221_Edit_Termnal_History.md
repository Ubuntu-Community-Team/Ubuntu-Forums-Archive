---
title: "Edit Termnal History"
date: 2012-06-25
forum: General Help
---

### Post by jmfal on 2012-06-25
I would like to edit my terminal history(command).

Is there a way to delete multiple instances of the same command.

Example:  conky,  killall conky, sudo apt-get update.

I found a thread that said to edit the .bashrc file but I  don't know what to enter or change.

---

### Post by sgage on 2012-06-25
> **jmfal said:**
> I would like to edit my terminal history(command).

Is there a way to delete multiple instances of the same command.

Example:  conky,  killall conky, sudo apt-get update.

I found a thread that said to edit the .bashrc file but I  don't know what to enter or change.

In your home directory is a file called... (wait for it...) 

.bash_history

That's the file you want to edit.

---

### Post by jmfal on 2012-06-25
That did it.

History was getting full.

You have to delete the command, commenting out with "#" just puts a "#" in front of the command.  

Thanks for the help      [SOLVED]

---

### Post by haqking on 2012-06-25
> **jmfal said:**
> That did it.

History was getting full.

You have to delete the command, commenting out with "#" just puts a "#" in front of the command.  

Thanks for the help      [SOLVED]

you can change the size of the history.

You can also just clear it with
```

history -c
```

cheers

---

### Post by jmfal on 2012-06-25
Thanks for the advice.
I use the history to copy/paste for myself and here in the forum, it eliminates entering incorrecly, 

I seen the size in the .bashrc file, mine is set at 2000, but I wasn't sure if you can edit that file.

---

