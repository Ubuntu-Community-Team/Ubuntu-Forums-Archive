---
title: "Sort command without arguments?"
date: 2009-12-12
forum: General Help
---

### Post by Cosmogirl on 2009-12-12
Hi,

This is probably a really stupid question but I can't seem to find the answer on the Internet or in the man pages.

I'm a beginner trying to learn to use the command line.  As an experiment today I typed 'sort' without options or arguments.  Then whatever else I typed (for example, pwd then enter) just got reproduced on screen as standard input instead of being interpreted as a command.  I have figured out that this means that every line that I produced will be sorted alphabetically once I indicate that I have finished providing input.  However I don't know how to tell bash that I've finished providing input so that the sort command will be executed.

Am I right about this & if so, what's the command to tell bash to sort the lines & bring the command prompt back to the screen?

Thanks for your help.

---

### Post by darthmob on 2009-12-12
You can cancel almost everything in command line with CTRL+c.

I guess that sort doesn't do anything if you start it without at least one argument. The man page says it needs one or more text files it is supposed to sort. ;)

---

### Post by Rinzwind on 2009-12-12
> **Cosmogirl said:**
> Hi,

This is probably a really stupid question but I can't seem to find the answer on the Internet or in the man pages.

I'm a beginner trying to learn to use the command line.  As an experiment today I typed 'sort' without options or arguments.  Then whatever else I typed (for example, pwd then enter) just got reproduced on screen as standard input instead of being interpreted as a command.  I have figured out that this means that every line that I produced will be sorted alphabetically once I indicate that I have finished providing input.  However I don't know how to tell bash that I've finished providing input so that the sort command will be executed.

Am I right about this & if so, what's the command to tell bash to sort the lines & bring the command prompt back to the screen?

Thanks for your help.

ctrl-c to quit the command 'sort'.

As soon as you add a text file after sort it will give command line back after showing the sorted lines (or if you redirect to a files after that new file is done).

---

### Post by hal10000 on 2009-12-12
CTRL-C quits the command without executing it, but if you want to execute the command after typing the lines that have to be sorted you need to type **CTRL-D**

---

### Post by Cosmogirl on 2009-12-13
Thanks for your help guys.  In fact hal10000 was right: control-D turned out to be what I wanted.  It sends an End-of-file message which tells sort to get on with the job.  Although control-C is good to know too.

---

