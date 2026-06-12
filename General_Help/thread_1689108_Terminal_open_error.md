---
title: "Terminal open error"
date: 2011-02-16
forum: General Help
---

### Post by 4brunu on 2011-02-16
hey, i have an "error", its not really and error, every time I open the terminal, it shows this:

Reading: command not found
Building: command not found
Reading: command not found
*****@****-****:~$

anyone can help me with this?

cumps

---

### Post by Brandon Williams on 2011-02-16
Somewhere in your .bashrc or .profile, you probably have some line (maybe they should be comments?) that begin with the words "Reading" and "Building". Since "Reading" and "Building" are not known commands, you see errors reported.

---

### Post by AlphaLexman on 2011-02-16
> **Brandon Williams said:**
> Somewhere in your .bashrc or .profile, 
Or it could be in ~/.bash_profile 

**NOTE:** The squiggly-slash (~/) means your own users directory in '/home' and the dot (.) before the filename means it is a hidden file. To see hidden files in nautilus (the default file manager), hit 'ctrl-h' or in a terminal use ```
ls -a
```

> you probably have some line that begin*(s)* with the words "Reading" and "Building".
[INDENT][/INDENT]+1 ^

---

### Post by 4brunu on 2011-02-16
Problem solved, you two have reason on the cause of the problem, thanks :)

---

