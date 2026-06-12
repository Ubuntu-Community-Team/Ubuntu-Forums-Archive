---
title: "Making script files executable"
date: 2010-06-01
forum: General Help
---

### Post by Stord on 2010-06-01
I would like to make lisp files executable. Ie. i can go like this on the command prompt

./hello.lisp

and it would invoke a .sh script on hello.lisp which would cause the file to execute. 

Any way to do this?

---

### Post by PeEllAvaj on 2010-06-01
What lisp distribution do you use?  If you used clisp, you could make the following file as hello.lisp.

```
#!/usr/bin/clisp
(print
  "HELLO WORLD")

```

This file can then be run as "./hello.lisp". (assuming the executable flag was set)

---

### Post by towheedm on 2010-06-01
You can make a script executable by setting the executable flag:

```
sudo chmod +x filename
```

---

### Post by Stord on 2010-06-01
Im targetting sbcl and ecl lisp on this one. I would actually want to probably execute a script or something which parses the arguments.

So im guessing i will need something like
#!my-script arg1 arg2
at the top? 

Any references for the #! syntax?

Would it be advisable to make all lisp files executable? I dont see any problem with it, how would i do that?

Thanks !

---

### Post by PeEllAvaj on 2010-06-01
You can learn more about the #! (shebang) on wikipedia at [http://en.wikipedia.org/wiki/Shebang_(Unix](http://en.wikipedia.org/wiki/Shebang_(Unix)).

In theory (not familiar with those lisp distros), you will just put your lisp interpreter at the top:
```
#!/usr/bin/ecl
```

Any arguments would be passed in like "./file.lisp arg1 arg2" when running the app, and then be accessible via your lisp program.

---

### Post by Stord on 2010-06-02
Cool, thanks all, that pretty much answers all my questions :)

---

