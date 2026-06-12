---
title: "extract .rar file"
date: 2010-09-06
forum: General Help
---

### Post by nishant29 on 2010-09-06
hi..

i am not able to extract .rar file contents please tell me how to do that..

---

### Post by Zubb on 2010-09-06
Click software at the top and choose Ubuntu software centre.
Search "rar" and install:- "RAR"
Once installed, go back to your .rar file, right click and select "extract here"

Or you can do it from the terminal/Shell
Click application > accessories > terminal.

Then change directory to your .rar file
Input:-
tar -xvf *****.rar
Change ***** to your file name.

---

### Post by nishant29 on 2010-09-06
thnks but tell me one more thing i am new to ubuntu so please tell me how to change directory from terminal

---

### Post by TNT1 on 2010-09-06
> **nishant29 said:**
> thnks but tell me one more thing i am new to ubuntu so please tell me how to change directory from terminal

# cd "directory"

remember, ubuntu is case specific though, as in Documents, not documents...

---

### Post by WorMzy on 2010-09-06
```
cd
```

You can change to a relative directory, or an absolute directory. To change to a relative directory, type the path from your current location, without the preceding slash. e.g.

```
cd Documents/project/report
```
Assuming you started in ~ (which is /home/<your username>), this command will change your shell's directory to /home/<your username>/Documents/project/report.

To change to an absolute directory, you just type the absolute address after cd. e.g.
```
cd /etc/gtk-2.0/
```

Use
```
ls
```
to get a list of files and folders in your current directory, or
```
ls <relative path|absolute path>
```
e.g.
```
ls Documents
```
or
```
ls /etc
```

---

### Post by dino99 on 2010-09-06
into console: cd /path-to-your-new-dir/

by default ubuntu has its archive extractor you can run by right clicking on the package to extract

more info below

---

### Post by BbUiDgZ on 2010-09-06
> **nishant29 said:**
> thnks but tell me one more thing i am new to ubuntu so please tell me how to change directory from terminal
just another wee tip when using terminal, TAB will auto complete

---

### Post by ender4 on 2010-09-06
also, ".." expands to the parent of the current directory, "." expands to the current directory, and "~" expands to your home directory (that is /home/<user name>/)

---

