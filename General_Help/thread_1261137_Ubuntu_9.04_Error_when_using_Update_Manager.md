---
title: "Ubuntu 9.04 Error when using Update Manager"
date: 2009-09-08
forum: General Help
---

### Post by rahowill on 2009-09-08
I am receiving the following error message:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
Does E: refer to a drive?
I am a newbie and will greatly appreciate any help or insight into the cause for this error.  Thank you.

---

### Post by drs305 on 2009-09-08
No, don't worry about the E: - I believe it refers to *Error*

Applications, Accessories, Terminal to open a terminal.
Type:
```

sudo dpkg --configure -a

```
It will ask for your password. Type it and press ENTER. You won't see anything as you type it.

You can learn about commands by typing "man <command>" in a terminal. 
Example:  man dpkg


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by rahowill on 2009-09-08
Thank you DRS305.  I had to run additional code that was provided to me from another users post in Linux Questions.  I then ran the code that you suggested and everything installed!  Thanks again.

---

### Post by t0p on 2009-09-08
**rahowill:** I thought I'd just tell you something that may seem obvious.  Then again, maybe it *isn't* so obvious, considering how often I see this question posed in these forums.

When an error message says that you should run a particular command, it's generally a good idea to follow the suggestion and run the command.

For example: in this instance, the error message said:

> you must manually run 'sudo dpkg --configure -a' to correct the problem.

So the correct course of action was to open a terminal and type in:

```
sudo dpkg --configure -a
```

Do take notice of what error messages say.  A programmer went to the trouble of writing the message; and you can be pretty sure he wrote it for a reason...

---

