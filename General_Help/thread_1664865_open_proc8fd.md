---
title: "open /proc/8/fd"
date: 2011-01-11
forum: General Help
---

### Post by borgward on 2011-01-11
How do I change permissions to open /proc/1 thru all/fd at once? In my case, that would be 1 thru 3357

---

### Post by hawkmage on 2011-01-11
Why are you trying to to read all of the file descriptors for all of the processes on you system?

---

### Post by borgward on 2011-01-11
No Particular reason. Just curious. I just want an honest un censored answer.

To be helpful, I want to look at /proc/<PID>/fd. In other words, I want to see the contents of /fd in all processes.

---

### Post by hawkmage on 2011-01-11
I have never tried to change the permissions anything under /proc/# and it is probably not a good idea.  

/proc is a virtual file system mapping information about processes and certain devices into a directory structure for easy reference.  Many of the items like the file descriptors are read only items that you can not change.

---

### Post by borgward on 2011-01-11
I agree that it is a dangerous idea.

So, how do I change the permissions to read? I am not interested in writing. Do you know how to do that?

---

### Post by hawkmage on 2011-01-11
You can not change the permissions.  The objects them selves are read only, it is like trying to change the permissions on a file on a CD-ROM.  

To read them you have to be root.  To see what is in /proc/8/fd run the command:
```
sudo ls -l /proc/8/fd
```

---

