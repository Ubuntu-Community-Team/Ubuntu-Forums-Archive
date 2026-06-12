---
title: "Archive Mounter for .iso"
date: 2011-07-17
forum: General Help
---

### Post by mklcst on 2011-07-17
Hi,
I am trying to mount an iso with Archive Mounter. It works but I can't see it in /media.
What's the problem with that?:popcorn:

---

### Post by mikejonesey on 2011-07-17
~/.gvfs

---

### Post by mklcst on 2011-07-17
I'm sorry I am not an expert, can you explain me what I have to do?

---

### Post by mikejonesey on 2011-07-17
~/ = your home dir

.gvfs = a hidden directory in your home dir

```
cd ~/.gvfs
```

:)

---

### Post by mklcst on 2011-07-17
\\:D/

Thank you so much!!

---

### Post by wildmanne39 on 2011-07-17
Hi, also for hidden files in the home directory you can click on your home folder then hit ctrl+h and it will show you the files.

---

### Post by JamesTheAwesomeDude on 2012-11-13
Hey, if you want it to mount in /media (or anywhere else,) type this:
```
sudo mount -o loop <file>.iso /media
```Now I need to know how to unmount it... :(

---

### Post by oldos2er on 2012-11-13
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

