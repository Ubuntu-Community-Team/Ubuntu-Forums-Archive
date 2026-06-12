---
title: "Is there an environment variable for the Trash?"
date: 2010-04-22
forum: General Help
---

### Post by dodle on 2010-04-22
(repeat question here) :P

---

### Post by kerry_s on 2010-04-22
i'm not sure i understand, what is it you want to do?

---

### Post by beren.olvar on 2010-04-22
I think you need to be more specific.
If you are looking for the actual place where your Trash is stored, look at
~/.local/share/Trash/
there are 2 directories "files"; with the actual files, and "info"; with the necessary information to recover those files.

---

### Post by dodle on 2010-04-22
Okay, sorry, I'll be more specific.  But then this thread will probably have to be moved to the "Programming Talk" section.  

I wrote a script in Python.  One of its functions is to send files to the trash.  But I haven't found a method in Python's documentation to automatically move files to the trash bin.  The only methods I have found delete the files, bypassing the trash.  Neither have I found a system command to do this.  "rm" and "rmdir" bypass the trash as well.  So at the moment, my script has to do a search for the trash from a list of possible directories, then manually move the files.

Here is the problem I am facing with this:  I only know of two possible trash locations from my experience with Ubuntu: ~/.local/share/Trash and ~/.Trash.  If this script is run on a different Linux distro, the trash may be in a different location.  If all Linux distros had an environment variable for the trash, then I could just specify that variable in my script and have the files sent there.

---

### Post by sisco311 on 2010-04-22
You can use gvfs-trash or trash (from the trash-cli package).

EDIT: /usr/bin/trash is a python script.

[http://en.wikipedia.org/wiki/Recycle_bin_(computing)#Implementations](http://en.wikipedia.org/wiki/Recycle_bin_(computing)#Implementations)
[http://www.ramendik.ru/docs/trashspec.html](http://www.ramendik.ru/docs/trashspec.html)

---

### Post by dodle on 2010-04-22
Thanks sisco, I can't believe I didn't know that.  I'm going to use the gvfs-trash.

**Edit:** Wow, that made my life so easy.

---

