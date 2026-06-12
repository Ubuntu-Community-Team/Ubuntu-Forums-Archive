---
title: "Installing software from source"
date: 2011-09-13
forum: General Help
---

### Post by QuickSphinx on 2011-09-13
Hi everyone,

I'm trying to downoad the latest version of Mednafen (which I could only find from source) and am wondering if someone could enlighten me on the process of doing so.

More specifically where the application goes after I run the installing process and why I'm receiving errors upon running "make" :
```

make[2]: Entering directory `/home/dylan/Desktop/mednafen/src/hw_cpu'
/bin/bash ../../libtool  --tag=CC   --mode=link gcc -DC68K_GEN -fsigned-char  -Wall -Winline -Wshadow -Wempty-body -Wignored-qualifiers  -fomit-frame-pointer -finline-limit=6000 --param large-function-growth=800 --param inline-unit-growth=175 --param max-inline-insns-single=10000 -fno-strict-overflow -I -g -O2  -DC68K_GEN  -o gen68k c68k/gen68k-c68kexec.o c68k/gen68k-c68k.o c68k/gen68k-gen68k.o  -lsndfile   -lcdio -lm   -lz -lrt  -lz  -lasound -lm -ldl -lpthread -lSDL_net
../../libtool: line 308: syntax error near unexpected token `}'
../../libtool: line 308: `        echo "local: *; };" >> $output_objdir/$libname.ver~'
make[2]: *** [gen68k] Error 2
make[2]: Leaving directory `/home/dylan/Desktop/mednafen/src/hw_cpu'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dylan/Desktop/mednafen/src'
make: *** [all-recursive] Error 1


```

EDIT: Here is the link to the download: [http://forum.fobby.net/index.php?t=msg&th=659&start=0&](http://forum.fobby.net/index.php?t=msg&th=659&start=0&)

---

### Post by FormatSeize on 2011-09-13
For whatever reason, your computer thinks that the package is already installed. From my experience, I get the "all recursive" make error if I've already installed something and accidently tried to reinstalled it.

---

### Post by QuickSphinx on 2011-09-14
Thanks for your reply,

Do you have any Idea where I could find the software?

---

### Post by raja.genupula on 2011-09-14
look in software center or synaptic package manager

---

### Post by QuickSphinx on 2011-09-14
> **raja.genupula said:**
> look in software center or synaptic package manager

Neither!

---

### Post by raja.genupula on 2011-09-14
[http://packages.ubuntu.com/it/natty/mednafen](http://packages.ubuntu.com/it/natty/mednafen)


all the best

---

