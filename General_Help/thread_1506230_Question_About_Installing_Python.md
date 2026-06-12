---
title: "Question About Installing Python"
date: 2010-06-10
forum: General Help
---

### Post by Th3Professor on 2010-06-10
I'd like to install python "locally" (within my /home) while also "bypassing" the server's root-based installation of python, and without requiring either root access or sudo access.

How do I do that?

The server is running centos, though I figured the install steps could probably be the same if the package is uncompressed first and compiled from source.

I've tried googling it and so far have come up with something about "make altinstall". And there might be the option of using the "--prefix=" flag. I don't know if I'd need only one of those, or both, or something else entirely.

Thanks!

---

### Post by Th3Professor on 2010-06-27
2 week bump

---

### Post by WorMzy on 2010-06-27
After running ./configure and make, you'll have a fully working executable in the folder you ran it in, just use that instead of running "sudo make install".

Since it's not "installed", you'll need to use a full path to launch it.  (rather than just "python" you'll need to run ~/path/to/python

---

