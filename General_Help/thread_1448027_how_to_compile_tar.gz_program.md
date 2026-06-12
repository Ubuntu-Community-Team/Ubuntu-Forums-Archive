---
title: "how to compile tar.gz program"
date: 2010-04-06
forum: General Help
---

### Post by Milenkonslisboa on 2010-04-06
This is what I get when I install it:

milenko@hp6830s:~$ tar xvzf /home/milenko/programi/rayinvr.tar.gz
rayinvr/
rayinvr/rayinvr/
rayinvr/rayinvr/adjpt.f
rayinvr/rayinvr/atrc.f
rayinvr/rayinvr/blkdat.f
rayinvr/rayinvr/calmod.f
rayinvr/rayinvr/hdw.f
rayinvr/rayinvr/inv.f
rayinvr/rayinvr/main.f
rayinvr/rayinvr/misc.f
rayinvr/rayinvr/plt.f
rayinvr/rayinvr/rngkta.f
rayinvr/rayinvr/trc.f
rayinvr/rayinvr/rayinvr.com
rayinvr/rayinvr/rayinvr.par
rayinvr/rayinvr/Makefile
rayinvr/tramp/
rayinvr/tramp/adjpt.f
rayinvr/tramp/amp.f
rayinvr/tramp/atrc.f
rayinvr/tramp/blkdat.f
rayinvr/tramp/calmod.f
rayinvr/tramp/hdw.f
rayinvr/tramp/main.f
rayinvr/tramp/misc.f
rayinvr/tramp/plt.f
rayinvr/tramp/rngkta.f
rayinvr/tramp/trc.f
rayinvr/tramp/tramp.com
rayinvr/tramp/tramp.par
rayinvr/tramp/Makefile
rayinvr/vmodel/
rayinvr/vmodel/blkdat.f
rayinvr/vmodel/main.f
rayinvr/vmodel/misc.f
rayinvr/vmodel/plt.f
rayinvr/vmodel/test.f
rayinvr/vmodel/vmodel.com
rayinvr/vmodel/vmodel.par
rayinvr/vmodel/Makefile
rayinvr/pltsyn/
rayinvr/pltsyn/blkdat.f
rayinvr/pltsyn/main.f
rayinvr/pltsyn/misc.f

---

### Post by lisati on 2010-04-06
A .tar.gz file is an archive file, as is a .zip file. What the tar command you used did was extract the files into your home folder. There should be installation instructions on the website from which you downloaded the file.

---

### Post by Bradtek on 2010-04-06
As mentioned above you have only Extracted the contents of the archive

It's a little hard to tell you exactly how to install it when you do not mention what it is or where you got it.

but generally you would  cd to the directory it extracted to and type
```
./configure

make

sudo make install
```

---

### Post by lordskid on 2010-04-06
since most ends in .f I think it is a fortran code. make sure you have a fortran compiler and a c compiler. then try to to a make command. as there is a makefile. you might want to check online for the correct instructions as some programs require configuring before compiling. I don't see a configure script though. so make and make install will do or you have to configure the program manually.

---

### Post by Milenkonslisboa on 2010-04-06
Yes,It is a fortran 77 code.Actually it is a ray tracing program in geophysics.I have a problem in compiling it because main.f for example can not be compiled,some variables in it are defined in rayivr.par and rayinvr.com.

---

### Post by Milenkonslisboa on 2010-04-06
Do not know how to solve it.

---

### Post by 3rdalbum on 2010-04-06
The website says that there's a patch that you must use to get it to work on Linux. I don't know if this is still necessary, but you could try it.

---

### Post by Milenkonslisboa on 2010-04-06
milenko@hp6830s:~/rayinvr$ ./configure
bash: ./configure: No such file or directory

---

### Post by 3rdalbum on 2010-04-06
> **Milenkonslisboa said:**
> milenko@hp6830s:~/rayinvr$ ./configure
bash: ./configure: No such file or directory

There's no 'configure' file, so skip that step.

```
make
sudo make install
```

---

### Post by JoelOl75 on 2010-04-07
Some source also calls configure Configure (Capital "C") so check for that as well.

---

### Post by Milenkonslisboa on 2010-04-07
milenko@hp6830s:~/rayinvr$ sudo make install rayinvr
make: *** No rule to make target `install'.  Stop.
milenko@hp6830s:~/rayinvr

I still don't get it.

---

### Post by spibou on 2010-04-07
> **Milenkonslisboa said:**
> milenko@hp6830s:~/rayinvr$ sudo make install rayinvr
make: *** No rule to make target `install'.  Stop.
milenko@hp6830s:~/rayinvr

What did you get after you did```
make
```and before you did```
sudo make install
```? If **make** did not produce any error messages then you probably already have a compiled programme.

---

### Post by spibou on 2010-04-07
> **3rdalbum said:**
> There's no 'configure' file, so skip that step.

```
make
sudo make install
```
It should be said that one should *not* do **sudo make ...** unless they really trust the source of the code. A makefile can execute arbitrary code including erasing the whole hard disk or installing a rootkit. Furthermore I suspect that for a programme like this there is only going to be one executable so after **make** one can simply do```
cp -i  executable /usr/bin/executable
chmod 755 /usr/bin/executable
```where "executable" should be replaced everywhere by the actual name of the executable.

---

