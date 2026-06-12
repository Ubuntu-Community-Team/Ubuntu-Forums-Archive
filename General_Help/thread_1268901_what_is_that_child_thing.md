---
title: "what is that child thing"
date: 2009-09-17
forum: General Help
---

### Post by gnilaeh on 2009-09-17
i`ve seen it a number of times on the o/s. 
also, does it incorperate files on windows files?

---

### Post by doas777 on 2009-09-17
what?

---

### Post by The Cog on 2009-09-17
> **gnilaeh said:**
> i`ve seen it a number of times on the o/s. 
also, does it incorperate files on windows files?

I have no idea what you are talking about. Can you explain?

---

### Post by jerrrys on 2009-09-17
this what your talking about?

[http://manpages.ubuntu.com/manpages/jaunty/man2/fork.2.html](http://manpages.ubuntu.com/manpages/jaunty/man2/fork.2.html)

---

### Post by gnilaeh on 2009-09-17
ok. sorry for taking so long. was doing some research on what i was looking for.
a inherited user was put into my windows o/s folders. the inherited user i`d had child inside of it so i thought of ubuntu. my question now is,
how can i delete that inheritance from windows account, folders ect?
 
i started searching the forum.  it is inherited permissions that is in my windows o/s from ubuntu.

---

### Post by tgalati4 on 2009-09-17
man chmod

Typically:

sudo chmod 755 file.txt

will change the file permission to read,write,execute for the owner, and read,execute for group and others.
 
sudo chmod -R 755 /directorythatneedsfixing

This will change all the files inside the directory, including the directory itself.

---

