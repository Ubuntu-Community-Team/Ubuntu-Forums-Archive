---
title: "Running a script at the start of session"
date: 2009-12-11
forum: General Help
---

### Post by enoyhs on 2009-12-11
Hello!
**I would like to know how to run a script after I start the session (Log-in)**.

Why?
I have a homework assignment where I need to customize LiveCD. One of customizations is that I need to create a folder on a Desktop named *enoyhs*. But from what I read, only way to do this is to run a script at the start of session which then creates a folder on a desktop.
I imagine script would look like this:
```
mkdir ~/Desktop/enoyhs
```
The sad part is I can't get it to work. I have tried many methods I found on this forum, but none of them seem to work.

Thanks for your help in advance.

---

### Post by john newbuntu on 2009-12-11
Hmm. Homework eh.  Here's a hint: /etc/X11/Xsession.d

---

### Post by enoyhs on 2009-12-11
Thanks!

It worked :)

---

