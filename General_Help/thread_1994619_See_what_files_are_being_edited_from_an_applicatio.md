---
title: "See what files are being edited from an application"
date: 2012-06-03
forum: General Help
---

### Post by hakermania on 2012-06-03
I was wondering whether it is possible to launch an application within another application-inspector, while the latter is watching the former what files the former edits.

I want this so as to make it easier for me to know what each program does without inspecting the code and spending hours on this.

Thanks in advance for any answer!

---

### Post by 3rdalbum on 2012-06-03
I think this is possible, but I don't currently have enough knowledge to be able to tell you exactly how.

When Linux opens a program, the program gets represented in the /proc filesystem by a folder. This folder contains references to all the files currently open for reading or writing by that program. If you get the process ID of the program, you can literally use your file browser to look inside the program's folder in /proc and see what files are being used.

---

### Post by hakermania on 2012-06-03
> **3rdalbum said:**
> I think this is possible, but I don't currently have enough knowledge to be able to tell you exactly how.

When Linux opens a program, the program gets represented in the /proc filesystem by a folder. This folder contains references to all the files currently open for reading or writing by that program. If you get the process ID of the program, you can literally use your file browser to look inside the program's folder in /proc and see what files are being used.

Thanks for the answer. The thing is, I don't really want to know which files are open right now (because writing to files using e.g. C is super fast, especially if you add a line and such), but which files were edited from the start of the program till the end of it.

---

### Post by traditionalist on 2012-06-03
This should do what you want;

[http://linuxpoison.blogspot.de/2010/11/real-time-file-monitoring-file-watcher.html](http://linuxpoison.blogspot.de/2010/11/real-time-file-monitoring-file-watcher.html)

---

### Post by hakermania on 2012-06-03
> **traditionalist said:**
> This should do what you want;

[http://linuxpoison.blogspot.de/2010/11/real-time-file-monitoring-file-watcher.html](http://linuxpoison.blogspot.de/2010/11/real-time-file-monitoring-file-watcher.html)

No, it actually doesn't!
I know how to do this both in C++ and in bash, but I'm not interested in that.

How would I add the files I want to monitor while I have no idea which files are being edited/were edited?

---

### Post by traditionalist on 2012-06-03
> **hakermania said:**
> No, it actually doesn't!
I know how to do this both in C++ and in bash, but I'm not interested in that.

How would I add the files I want to monitor while I have no idea which files are being edited/were edited?

You must know where those files are. Monitor the directory(s).

---

### Post by hakermania on 2012-06-03
> **traditionalist said:**
> You must know where those files are. Monitor the directory(s).

No. I don't really know.

---

