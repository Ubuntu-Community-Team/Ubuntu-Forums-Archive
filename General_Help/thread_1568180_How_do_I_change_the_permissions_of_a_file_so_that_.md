---
title: "How do I change the permissions of a file so that it is executapble?"
date: 2010-09-04
forum: General Help
---

### Post by searchfgold6789 on 2010-09-04
I have an exe file I want to run under wine, but it's not letting me because the file permissions do not say it is executable...How do I get this to work?

---

### Post by WiReIs on 2010-09-04
Right click file > properties > permissions > tick exe box

---

### Post by amac777 on 2010-09-04
If it's a windows exectuable, you may also try right clicking the file and then -> "Open with Wine"

---

### Post by jeight on 2010-09-04
Same as first post. The box will say 'allow executing file as program'.

---

### Post by cinohpa on 2010-09-04
I've never heard of that happening. Windows doesn't use the executable bit to even determine whether things can be run or not.

Do you have sufficient privileges in the file system that you are trying to run it from? Is there any place you can "sudo" things to try and make it work.

Also, in general to make a file executable, the command is:

```
sudo chmod +x FILENAME
``` 

And you should run it from the directory that the file is in or specify an absolute path.

OOPS. Guess I don't really know much about wine.

---

