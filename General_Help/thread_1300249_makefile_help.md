---
title: "makefile help"
date: 2009-10-24
forum: General Help
---

### Post by vttay03 on 2009-10-24
I'm trying to install the newest version of vobcopy (not the version found in the repositories).  I've downloaded the files and put them into a directory.  I then run the following command from the shell:

```

sudo make install

```

However, I get the following output after an unsuccessful build - being somewhat new to Linux my ignorance is showing here...can anyone point me in the right direction?

```

install -d -m 755 //usr/local/bin
install -d -m 755 //usr/local/man/man1
install -d -m 755 //usr/local/man/de/man1
install -d -m 755 //usr/local/share/doc/vobcopy
install -m 755 vobcopy //usr/local/bin/vobcopy
install: cannot stat `vobcopy': No such file or directory
make: *** [install] Error 1

```

---

### Post by Vaphell on 2009-10-24
installation from source usually goes like that:
./configure (creates config for compilation)
make (builds binaries)
make install (installs in the system)

look for readme file with instructions, it should clarify

---

