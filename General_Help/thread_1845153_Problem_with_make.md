---
title: "Problem with make"
date: 2011-09-16
forum: General Help
---

### Post by LoZioGuido on 2011-09-16
Hy 
I have a natty mounted on my 2 core laptop.

Everytime I try to compile a program i retrieve always the same error (after make command)

make: execvp: chmod: File name too long
make: *** [blib/lib/.exists] Error 127

I suppose that something doesn't work with make. I tried also to reinstall make without success...
Please any suggestion?
thanks
bye

---

### Post by seawolf167 on 2011-09-16
Can you post the terminal output from the following commands (changing the names to the appropriate entries)

```
cd /path/to/program_directory
ls
make -v
make program_name
```

---

### Post by LoZioGuido on 2011-09-16
ok

[COLOR="Red"]cd[/COLOR] /home/guido/Scrivania/ParsePDB

[COLOR="red"]ls[/COLOR]
COPYING  Makefile.PL  ParsePDB.pdf  ParsePDB.pm  testparser

[COLOR="red"]make -v[/COLOR]
GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.


the program instructions say:

The PDB parser itself is a Perl package, indicated by the extension .pm. To install the package globally
on your system, you can use the provided makefile to copy it to your library path. To do this, login
as root and follow the standard routine:
./perl Makefile.PL
make
make install

After doing [COLOR="red"]make[/COLOR] i retrieve the error reported previously

Thanks

---

