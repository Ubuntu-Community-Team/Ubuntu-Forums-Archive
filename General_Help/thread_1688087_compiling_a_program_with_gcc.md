---
title: "compiling a program with gcc"
date: 2011-02-15
forum: General Help
---

### Post by k94382 on 2011-02-15
How do I compile this program?
([http://sourceforge.net/projects/crunch-wordlist/files/crunch-wordlist/](http://sourceforge.net/projects/crunch-wordlist/files/crunch-wordlist/))
I have seen instructions that say

```
gcc -c crunch.c
gcc -lm -o crunch crunch.o
```

The first command goes fine for me but I get an error for the second command

```
crunch.o: In function `main':
crunch.c:(.text+0x4874): undefined reference to `pthread_create'
crunch.c:(.text+0x48b8): undefined reference to `pthread_detach'
collect2: ld returned 1 exit status
```

Can someone please help me with installing this program? Thanks,

---

### Post by ahsan101 on 2011-02-15
Your GCC is installed properly? and the program you are trying to compile has the proper required libraries? Its seems something is missing that GCC cannot continue, i am not good at programming but still i think some linked-file is missing...

---

### Post by anglican on 2011-02-15
> **k94382 said:**
> How do I compile this program?
([http://sourceforge.net/projects/crunch-wordlist/files/crunch-wordlist/](http://sourceforge.net/projects/crunch-wordlist/files/crunch-wordlist/))
I have seen instructions that say

```
gcc -c crunch.c
gcc -lm -o crunch crunch.o
```

The first command goes fine for me but I get an error for the second command

```
crunch.o: In function `main':
crunch.c:(.text+0x4874): undefined reference to `pthread_create'
crunch.c:(.text+0x48b8): undefined reference to `pthread_detach'
collect2: ld returned 1 exit status
```

Can someone please help me with installing this program? Thanks,Try:
```
gcc -lm -lpthread -o crunch crunch.o
```

H

---

### Post by k94382 on 2011-02-15
> **anglican said:**
> Try:
```
gcc -lm -lpthread -o crunch crunch.o
```

H

that worked! what does -lpthread do? also, I'm not able to get access to the crunch man page. any suggestions on how I can get the manpages working too?

---

### Post by anglican on 2011-02-16
> **k94382 said:**
> that worked! what does -lpthread do? also, I'm not able to get access to the crunch man page. any suggestions on how I can get the manpages working too?From the gcc man page:
> -llibrary
       -l library
           Search the library named library when linking.  (The second
           alternative with the library as a separate argument is only for
           POSIX compliance and is not recommended.)

           It makes a difference where in the command you write this option;
           the linker searches and processes libraries and object files in the
           order they are specified.  Thus, foo.o -lz bar.o searches library z
           after file foo.o but before bar.o.  If bar.o refers to functions in
           z, those functions may not be loaded.

           The linker searches a standard list of directories for the library,
           which is actually a file named liblibrary.a.  The linker then uses
           this file as if it had been specified precisely by name.

           The directories searched include several standard system
           directories plus any that you specify with -L.

           Normally the files found this way are library files---archive files
           whose members are object files.  The linker handles an archive file
           by scanning through it for members which define symbols that have
           so far been referenced but not defined.  But if the file that is
           found is an ordinary object file, it is linked in the usual
           fashion.  The only difference between using an -l option and
           specifying a file name is that -l surrounds library with lib and .a
           and searches several directories.To get man pages working you have a few options either:

1) Copy the man page to a location the "man" command already knows about e.g. /usr/share/man/man1

2) Permanently let "man" know about the location of your man pages by adding the directory they're in to your $MANPATH environment variable

3) Let the "man" command know where to look each time you run it using the -M option.

H

---

### Post by k94382 on 2011-02-16
> **anglican said:**
> From the gcc man page:
To get man pages working you have a few options either:

1) Copy the man page to a location the "man" command already knows about e.g. /usr/share/man/man1

2) Permanently let "man" know about the location of your man pages by adding the directory they're in to your $MANPATH environment variable

3) Let the "man" command know where to look each time you run it using the -M option.

H

thanks for the help so far. when I extract crunch2.9 I do not see any files called man.
also, how can I install the file so that crunch shows up when I enter "apt-cache search crunch"?

---

### Post by anglican on 2011-02-16
> **k94382 said:**
> thanks for the help so far. when I extract crunch2.9 I do not see any files called man.
also, how can I install the file so that crunch shows up when I enter "apt-cache search crunch"?OK, I've actually had a look at the program for you. The correct way to compile and install it is:
```
tar xvfz crunch-2.9.tgz
cd crunch-2.9
make
sudo make install

```Programs that install in this way are unknown to to package management software i.e. apt-cache will not know anything about it. To get around that problem you would need to package the program yourself - how to do that is beyond the scope of this thread. Take a look at:

[https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)

If you choose just to install as above, remember to keep the crunch-2.9 directory - you will need the Makefile in it to uninstall the program (should you ever need to).

H

---

### Post by mc4man on 2011-02-16
You could likely use checkinstall w/ that source if you wished.
If using the makefile you may wish to review where it's being installed to, not sure why the author choose /
(PREFIX      = /pentest/passwords/

---

### Post by k94382 on 2011-02-17
> **anglican said:**
> OK, I've actually had a look at the program for you. The correct way to compile and install it is:
```
tar xvfz crunch-2.9.tgz
cd crunch-2.9
make
sudo make install

```Programs that install in this way are unknown to to package management software i.e. apt-cache will not know anything about it. To get around that problem you would need to package the program yourself - how to do that is beyond the scope of this thread. Take a look at:

[https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)

If you choose just to install as above, remember to keep the crunch-2.9 directory - you will need the Makefile in it to uninstall the program (should you ever need to).

H

very nice. that worked. I can now run the program and can also see the manpages. thank you for your effort. I will definitely read the wiki too.

---

