---
title: "GDB not able to locate files"
date: 2010-09-30
forum: General Help
---

### Post by Blake401 on 2010-09-30
Hello, I am fairly new to programming and I am completely new to these  forums, so I am not sure if this is the correct spot for this topic, but  it seemed the most likely.

Anyway, the issue that I am having is that when running GDB, the program will execute perfectly fine if I allow it to run without breakpoints if I skip stepping through the function using the 'n' command, but it will provide me with the following error if I try to step through it: 

35        srand( time(NULL));
(gdb) s
time () at ../sysdeps/unix/sysv/linux/x86_64/time.S:32
32    ../sysdeps/unix/sysv/linux/x86_64/time.S: No such file or directory.
    in ../sysdeps/unix/sysv/linux/x86_64/time.S

This happens not just for time() but for every function that would be found in the included libraries.

I included stdlib in the code, and in fact this code works perfectly fine on another system using Ubuntu 10.04 and GDB.  The source paths are identical between these two machines as well ( $cdir:$cwd ).

If anyone could help me resolve this issue it would be greatly appreciated.

---

### Post by dino99 on 2010-09-30
if the path is correct , check for rights

[https://wiki.ubuntu.com/Backtrace](https://wiki.ubuntu.com/Backtrace)
[http://manpages.ubuntu.com/manpages/maverick/man1/gdb.1.html](http://manpages.ubuntu.com/manpages/maverick/man1/gdb.1.html)
[https://bugs.launchpad.net/ubuntu/+source/gdb?field.searchtext=&orderby=-date_last_updated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu/+source/gdb?field.searchtext=&orderby=-date_last_updated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

---

### Post by Blake401 on 2010-09-30
Thanks for your response!  Could you clarify what you mean by "check for rights"?  Backtrace just tells me about the call to Time().

---

### Post by psusi on 2010-09-30
Don't do that.

Why are you trying to step into the standard runtime library functions?  Worry about your code, not gcc's.  It can't find those files because you don't have the libc source code installed, nor should you need to.

---

### Post by Blake401 on 2010-09-30
Thank you!  That really clears the issue up for me :)

---

