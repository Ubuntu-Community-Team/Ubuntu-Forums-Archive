---
title: "Can't edit a file !?!?"
date: 2010-05-07
forum: General Help
---

### Post by anaconda on 2010-05-07
I have a really strange problem. I am trying to edit a C++ source file, but gedit wont allow me to save changes to it. Gedit says:
```
A file with the same name already exists. Please use a different name.
```
Right. Of course the file exists, I am trying to edit an existing file.

About the same happens with kate... Kate opens the file in read-only mode.

However, if I edit the same file with nano, editing and saving works. So the problem shouldn't be with access rights. Also "ls" shows rw rights to the file.

What could be the problem? I can use nano, but I would need the syntax highlightind, and other features of a better editor.

And whether I use sudo or not has no effect. The same happens with or without sudo, and I am the owner of the file.

PS. luckily I am still dual booting with Hardy. I can always go back.

Oh and this is a new installation of ubuntu 10.04

---

### Post by sylvester_0 on 2010-05-07
You can run a "lsof" on the file; maybe some other process is locking it? Also, you could strace the editors to see what's going on when you try to save the file. Nano does offer syntax highlighting BTW, but nothing beats gedit in my book.

Edit: Also, are you saving to a native filesystem (not NTFS or something funky, right?)

---

### Post by anaconda on 2010-05-07
> **sylvester_0 said:**
> You can run a "lsof" on the file; maybe some other process is locking it? Also, you could strace the editors to see what's going on when you try to save the file. Nano does offer syntax highlighting BTW, but nothing beats gedit in my book.

Edit: Also, are you saving to a native filesystem (not NTFS or something funky, right?)

Thanks for the reply.

I think it is something funky.. 
the file is on a cifs share in our server. Editing works with nano though, so it should work with others too.hmm.. syntax highlighting in nano. Interesting.

I will check the lsof, when I boot to the 10.04 next time. 

The problem might be related to different character encodings?

---

