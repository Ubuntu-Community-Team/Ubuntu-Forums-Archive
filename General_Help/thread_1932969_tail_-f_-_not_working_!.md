---
title: "tail -f - not working ?!?"
date: 2012-02-28
forum: General Help
---

### Post by surhne on 2012-02-28
Hi,
 
I run from xubuntu live cd (11.10), when I run the tail -f command it just hangs.
If I stop it and run it again I can see the file has progressed but it stucks again.
 
Running watch 'ls -l /var/log/messages' show a constant progressseion in file size, but tail -f simple refuzes to "follow".
 
Any idea ?

---

### Post by greenpeace on 2012-02-28
What does it do?  

Do you have sufficient permissions to read the file?

Any errors in the terminal?

---

### Post by surhne on 2012-02-29
I run it as root, so I get no permission denied error (or any other error)
 
It shows the last few lines of the file (like tail without parameters will do)
but it just won't "refresh" when new lines are written to the file.

---

### Post by surhne on 2012-02-29
stupid cow fs :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/882147](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/882147)
 
moved the log file from /var (overlay fs) to tmp (tmpfs) everything runs like a charm!

---

