---
title: "opening an 'executable' (not windows .exe)"
date: 2009-08-20
forum: General Help
---

### Post by loll12 on 2009-08-20
I downloaded a file that i need to use, and in the properties its listed as an 'executable' 

how do i run it, or and what command or whatever?

thanks.

---

### Post by vinnywright on 2009-08-21
what's the file type?

VINNY

---

### Post by doas777 on 2009-08-21
well, some executables can just be double-clicked. others need to be run via a runtime (these are usually scripts or java jars). if you right click the file and open it with a text editor, does it look like program code or gibberish?

---

### Post by bchurchill on 2009-08-21
You can try running it from a terminal:

```

cd /path/to/executable
./executable

```

You may need to give yourself execute permissions on the file, so you may need one or more of the following commands, possibly using sudo depending on whether you own the file:

```

chown <username> <filename>
chmod 755 <filename>

```

If you still have problems, post the output of 

```

ls -l | grep <filename>

```

and also

```

file <filename>

```

---

### Post by aldimond on 2009-08-21
If just opening the file (double-clicking or single-clicking or whatever does the trick in your GUI) doesn't work you might be able to get more hints about just what kind of executable it is by running 'file' on it.  If you can get a terminal open and navigate to the directory where it's located, issue the command 'file <filename>'.  For example:

```
aldimond@impulse:/usr/bin$ file X
X: setuid setgid ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped
```

There's a lot of junk there, but if it says either "ELF" or "a.out", the processor type matches yours (mine says "x86-64", which is indeed what I have), and it says "for GNU/Linux" or "for Linux" somewhere in there, it's probably a normal Linux program that you can just run.  It it says stuff about Java or archives you may have to do something else.

If it looks like a normal Linux program but clicking it does nothing, and you're already at the terminal you can try running it from there.  Just type ./ then the name of the program and hit enter.  It may print some useful info to the terminal.

---

### Post by neophyte_7 on 2009-08-21
I think the software 'wine' ll do it...??

---

### Post by loll12 on 2009-08-21
the code

cd /path/to/executable
./executable
worked perfectly... =]

i love ubuntu forums!

---

