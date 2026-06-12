---
title: "emacs21 broken"
date: 2006-02-14
forum: General Help
---

### Post by rplantz on 2006-02-14
emacs21 used to work for me. In fact, it was the default editor when I double-clicked on a text file. It no longer works.

When I try from the command line, I get
```

bob@ubuntu:~$ emacs21
No fonts match `-jmk-neep alt-medium-r-*-*-12-*-*-*-c-*-iso8859-1'
bob@ubuntu:~$

```

I've tried complete removal, then install again. I've searched Synaptic for jmk-neep. About the only think I can think of that may have messed it up is that I installed kubuntu-desktop to see what it looks like. But I've returned to gnome, and emacs21 is broken.

Another oddity is that emacs (without the 21) seems to work, but both emacs and emacs21 seem to be linked ultimately to the same program:
```

bob@ubuntu:~$ which emacs
/usr/bin/emacs
bob@ubuntu:~$ ls -l /usr/bin/emacs
lrwxrwxrwx  1 root root 23 2006-02-13 21:29 /usr/bin/emacs -> /etc/alternatives/emacs
bob@ubuntu:~$ ls -l /etc/alternatives/emacs
lrwxrwxrwx  1 root root 18 2006-02-13 21:48 /etc/alternatives/emacs -> /usr/bin/emacs21-x
bob@ubuntu:~$ ls -l /usr/bin/emacs21-x
-rwxr-xr-x  1 root root 6686456 2005-05-03 07:16 /usr/bin/emacs21-x
bob@ubuntu:~$

```
and
```

bob@ubuntu:~$ which emacs21
/usr/bin/emacs21
bob@ubuntu:~$ ls -l /usr/bin/emacs21
lrwxrwxrwx  1 root root 9 2006-02-13 21:29 /usr/bin/emacs21 -> emacs21-x
bob@ubuntu:~$

```
I suspect that one is bringing in a configuration file, while the other is not. But I still cannot figure it out.

---

### Post by thermans on 2006-02-14
Did you find "jmk-neep" in Synaptic?  

If not, check if you have a file called ".Xresources" or ".Xdefaults" in your home directory.

If you have either of those, I bet there is an entry in there that says:

```
Emacs*font: -jmk-neep alt-medium-r-*-*-12-*-*-*-c-*-iso8859-1
```

Either remove it completely to get the default font, or put another font in there that *does* exist on the system.

Whatever you do, run "xrdb .Xresources" or "xrdb .Xdefaults" (depending on which one you have).

That should take care of it.

---

### Post by rplantz on 2006-02-14
Thank you, it works.

What did I do? I was messing around with emacs font colors and created a new .Xresources file. Being a careful sort, I saved the old one as .Xresource_back. Simply reverting back to my backup fixed things. :oops:

---

