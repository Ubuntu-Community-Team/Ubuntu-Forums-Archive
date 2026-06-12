---
title: "Python script in /usr/local/bin won't run"
date: 2010-07-06
forum: General Help
---

### Post by Elding Nyr on 2010-07-06
Hi folks!

I am running Ubuntu 10.04 Lucid.

I recently wrote a script (hello.py) in Python and placed it in /usr/local/bin. The first line of the program is ```
#!/usr/bin/python
``` and I double-checked that it is marked as executable. Furthermore, I double checked that the newline character after the first line of the program was "\n" rather than "\r\n". If I use the commands "./hello.py" or "python hello.py" while in the /usr/local/bin directory, the script successfully executes, but if I move to an arbitrary directory and try either of these commands, I get "Command not found" and "No such file or directory" respectively.

Running "ls -l" in /usr/local/bin returns the following results:
-rwxr-xr-x 1 root    root       40 2010-07-06 15:00 hello.py

I have also double-checked that /usr/local/bin is listed when I run the command "echo $PATH".

Any ideas on why this isn't working? Need any further information to help with diagnosis? Thanks!

---

### Post by potat on 2010-07-06
When you are in an arbitrary directory, you can just type "hello.py" (rather than "./hello.py" and it should work. It should even tab-complete for you.

---

### Post by WorMzy on 2010-07-06
If it's not exectuing, then perhaps /usr/local/bin isn't in your PATH variable. Post the output of 'echo $PATH' here.

EDIT: Clearly I didn't read your original post very well. :P

---

### Post by DaithiF on 2010-07-06
Hi, and just to explain further:
```
./hello.py

```means execute hello.py in the current directory.
```
python hello.py

```means run python, and have it execute hello.py in the current directory
```
hello.py

```means search PATH and execute the first occurrence it finds of hello.py in one of the PATH directories.

---

### Post by whiskeylover on 2010-07-06
The "." in "./hello.py" is for current directory. Hence it doesn't work outside /usr/local/bin.

---

### Post by Elding Nyr on 2010-07-06
Thanks so much ladies and gents! That clears it up perfectly. In retrospect, a rather stupid mistake... :P

---

