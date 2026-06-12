---
title: "Porting terminal output to gedit"
date: 2010-10-30
forum: General Help
---

### Post by xshagy on 2010-10-30
I'm trying to port terminal output into gedit.
Example....

ls -l | gedit

This will open a blank gedit window but with non of the output from "ls -l".  Am I wrong thinking this should work?

I'm using,
GNOME Terminal 2.30.2
gedit 2.30.3
ubuntu 10.04

Thanks in advance.

---

### Post by llamabr on 2010-10-30
That won't work, because you're piping it to gedit.  That will make gedit try to run the output of ls.  You could do something like:

```
ls -l > text.txt && gedit text.txt
```

Or, you could use variables, if you don't want to call a particular file.  What are you hoping to accomplish?

---

### Post by xshagy on 2010-10-30
I'm just looking for a nicer way to view and temporarily save, terminal output.  I'd like to be able to scroll through it and save it if I want to.  Having the output in an unsaved text file would let me continue using the terminal while keeping certain outputs until I didn't want them anymore.

What you wrote is exactly what I would like; but it would be nice if I didn't have to create a new file.  A file I would have to manually delete later.

Any ideas?

---

### Post by xshagy on 2010-10-30
Using a variable seems like a good idea.  I'm assuming you're talking about something like this...

ls -l > $my_variable && gedit $my_variable

I'm not sure the right syntax though.

---

### Post by xshagy on 2010-10-31
Found another thread on the same topic

[http://ubuntuforums.org/showthread.php?t=1423708&page=2](http://ubuntuforums.org/showthread.php?t=1423708&page=2)

I'll mark this as solved.

---

