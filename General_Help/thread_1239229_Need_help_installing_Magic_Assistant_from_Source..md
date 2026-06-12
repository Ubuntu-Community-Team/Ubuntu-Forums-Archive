---
title: "Need help installing Magic Assistant from Source."
date: 2009-08-13
forum: General Help
---

### Post by redonwhite on 2009-08-13
Hello,

I'm trying to install Magic Assistant from source.  

[http://sourceforge.net/projects/mtgbrowser/](http://sourceforge.net/projects/mtgbrowser/)

I am following the directions on how to install software from source from the following link.

[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html)

Now the part I'm getting stuck on.  When I type ./configure I get this...

```
name@name:~/src/MagicAssistant$ ./configure
bash: ./configure: No such file or directory
```

I saw a folder called configuration in the MagicAssistant folder so I tried this...

```
name@name:~/src/MagicAssistant$ ./configuration
bash: ./configuration: is a directory
```


Any idea what i might be doing wrong?  Thanks for your help.  Here is a list of whats in the MagicAssistant Folder.

```
name@name:~/src/MagicAssistant$ ls
about_files  configuration  libcairo-swt.so  plugins
about.html   features       magicassistant
```

---

### Post by oldos2er on 2009-08-13
What happens if you type ./magicassistant ?

---

### Post by redonwhite on 2009-08-13
> **oldos2er said:**
> What happens if you type ./magicassistant ?

I get the following...in the code you can see I then type "make" and get no makefile.  I show the list of files currently in the folder.  thanks.

```
name@name:~/src/MagicAssistant$ ./magicassistant
name@name:~/src/MagicAssistant$ make
make: *** No targets specified and no makefile found.  Stop.
name@name:~/src/MagicAssistant$ ls
about_files  configuration  libcairo-swt.so  plugins
about.html   features       magicassistant   workspace
```

---

### Post by redonwhite on 2009-08-14
bump

---

### Post by redonwhite on 2009-08-14
Okay so an update.  

I went back to sourcforge and found a updated 64 bit file.  I downloaded that one and unpacked it.  I then ran ./magicassistant and the program loaded!!!.. whoohoo!!!....Now.  How do i create an icon or something of that nature so that i can access this program and use it?  thanks.

---

