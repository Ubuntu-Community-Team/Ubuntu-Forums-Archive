---
title: "Merging Folders"
date: 2009-07-23
forum: General Help
---

### Post by AxelMan0 on 2009-07-23
I feel like I should have been able to find another post about this but I haven't had any luck so I'll take the chance and start a new thread about it.  Is there any way to enable file merging similar to Windows? Occasionally (namely in terms of music organization) I will want to move a folder into the filesystem that is of identical name to another folder (in my case artist and/or album name). Linux either refuses to move the new folder or overwrites the old folder entirely rather than just adding the new files or replacing the files with similar names. Can this be changed by moving to a different file manager (such as dolphin) or is this a problem that requires some kernel modification? I'm hoping it's the first since I'm pretty new to Linux :).

---

### Post by kpkeerthi on 2009-07-23
I've used nautilus (Places -> Home) and it did prompt for 'Merge' when it found files/folder that have same names.

For a command line tool, try rsync. It has hundreds of command line switches and it might go way over your head to achieve what you need with it.
```
man rsync
```

---

### Post by bacil on 2009-07-23
i am using Krusader to do these operations. or comand line with diff

---

### Post by AxelMan0 on 2009-07-23
Thanks for the ridiculously fast responses! Problem solved

---

