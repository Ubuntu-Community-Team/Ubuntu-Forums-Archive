---
title: "using find and exec"
date: 2011-03-12
forum: General Help
---

### Post by PGScooter on 2011-03-12
Hi, I have a bunch of .caf files in a directory that I want to convert to ogg but I cannot figure out way to do it (except manually).
I want to do:
sox filename.caf filename.ogg

here is my attempt:

```

octavio@ubuntu:~/Desktop/Fly$ find -iregex .*caf -exec sox `basename {} .caf`{.caf,.ogg} \;
sox FAIL formats: can't open input file `./Fly13.caf.caf': No such file or directory
sox FAIL formats: can't open input file `./Fly14.caf.caf': No such file or directory
sox FAIL formats: can't open input file `./Fly09.caf.caf': No such file or directory
sox FAIL formats: can't open input file `./Fly312.caf.caf': No such file or directory
sox FAIL formats: can't open input file `./Fly346.caf.caf': No such file or directory
sox FAIL formats: can't open input file `./Fly99.caf.caf': No such file or directory
sox FAIL formats: can't open input file `./Fly709.caf.caf': No such file or directory

```

I don't know why basename is not taking off the extension.

thanks!

---

### Post by Vaphell on 2011-03-12
[http://www.linuxquestions.org/questions/programming-9/find-exec-syntax-bug-in-find-563261/](http://www.linuxquestions.org/questions/programming-9/find-exec-syntax-bug-in-find-563261/)

apparently basename is executed before the substitution for {} - basename sees '{}' which has no extension to drop so {} is left untouched, you glue extension to it ({}.ext) and then {} is replaced with file so you get filename.ext.ext. In that thread there are few workarounds mentioned.

---

### Post by PGScooter on 2011-03-12
thanks Vaphell!

I ended up using a script similar to the last post in the thread you linked to. Sometimes one tries to hard to do a one-liner.

---

