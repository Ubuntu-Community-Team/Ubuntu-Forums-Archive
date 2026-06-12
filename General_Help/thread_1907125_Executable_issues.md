---
title: "Executable issues"
date: 2012-01-10
forum: General Help
---

### Post by thomsmells on 2012-01-10
I'm trying to write a .desktop file to link to an executable (Cave Story specifically) in one of my directories, the issue I'm running into is it only seems to run properly when it's called from the terminal within its directory (./executable).

Trying to call it from within the terminal from any other directory using the full filepath or even clicking on it from file manager doesn't work (a black box appears, then vanishes and in terminal a few lines are produced, but the program doesn't run).

Any ideas why activity would be different depending on where I try to execute it from? And how I would solve this.

---

### Post by Buntumatic on 2012-01-10
Not Ubuntu user, thus not sure about .desktop files, have you tried to cd first?
```
cd /path/to/directory; ./executable
```

---

### Post by ajgreeny on 2012-01-10
Is the executable's directory in your $PATH folders?  If not you will need to use the full pathway to the executable, eg /home/user/executable, and you will also need to make sure that the file has executable set in its permissions.

---

### Post by sisco311 on 2012-01-10
In short, without going into details, it's a poorly written application. :)

Either use the Path key in the .desktop file to specify the directory:
```

[Desktop Entry]
Name=whatever
Comment=whatever
...
Exec=command
**Path=/full/path/to/dir**
...

```

Or start a sub-shell, cd into the directory and start the application: 

```

[Desktop Entry]
Name=whatever
Comment=whatever
...
Exec=sh -c "cd /full/path/to/dir && ./command"
...

```

You could also write a script:
```
#!/bin/sh

cd /path/to/dir && ./command

```

make it executable and put it in $HOME/bin or /usr/local/bin

---

### Post by thomsmells on 2012-01-11
Thanks! The sub shell did the trick. :D

---

