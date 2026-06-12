---
title: "dd"
date: 2009-09-20
forum: General Help
---

### Post by brusegadi on 2009-09-20
Hello everyone.  First off, thanks for everyone for your help.  Now, to my question: I was playing around with dd and I ran the following:  dd if=/dev/zero bs=1000     (I killed it) dd if=/dev/zero bs=1000 count=400  I learned that this writes to stdout.  What does that mean?  Are there now files floating around that I have to look for and delete?  I eventually figured out that what I wanted to do was more like:  dd if=/dev/zero count=40000000 f=temp    (I wanted to wipe a portion of my drive where I was going to install something on, so a created this temp to not have to wipe the entire thing, props to anyone who can tell of an easier way of accomplishing this.)

---

