---
title: "Running a program with command line arguments?"
date: 2011-10-24
forum: General Help
---

### Post by Scarbird on 2011-10-24
I was just wondering, how do you run a program with command line arguments like that "-set whatevergoeshere 1" stuff.

---

### Post by papibe on 2011-10-24
Hi Scarbird. Welcome to the forums!

Different applications have different options. It is easier to explain through examples.

This list the content of the current directory:
```
ls
```
with the option -l you change the output format:
```
ls -l
```
Is that what you are looking for?
Regards.

---

### Post by xianbei on 2011-10-24
scarbird, welcome.

many programs can be run from the command line, and many of them take arguments. take firefox for example:

open a terminal and type

```
firefox "www.myspace.com/osageorangemusic"
```

one of the most useful tools in ubuntu (linux in general) is the man function from the bash (terminal):

papibe's suggestion of 'ls' is a good start. type this to find out how to use it with command line arguments:

```
man ls
```

i hope that helps.

---

### Post by emiller12345 on 2011-10-25
many programs also have help built right into them. Usually it's
```
command -h
``` or ```
command --help
```

---

