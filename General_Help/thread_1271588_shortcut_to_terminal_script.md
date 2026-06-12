---
title: "shortcut to terminal script?"
date: 2009-09-21
forum: General Help
---

### Post by z80 on 2009-09-21
in windows you can create a schortcut and in the file location field you can put terminal/dos commands and when you double click the shortcut it would automaticaly run the dos commands very quickly and effiecently.  is there a way to do this in ubuntu?  still a newb to linux and have now had to reinstall it 5 or 6 times cause i keep screwing it up with bad terminal commands and playing with the wrong settings, the wrong ways.  i want a icon on my desktop that i can double click and have it pop open a terminal and execute a command or two and then close the terminal window.  i dont even need the terminal window i just need the command run when i double click and id rather not have to enter a password to let the command execute....
any ideas?
thanks

---

### Post by juancarlospaco on 2009-09-21
a bash script, the file extension of bash script is:
**.sh**

It need execution permission, so it can be executed.

Then make a launcher containing:

**sh /path/to/your/script/scriptname.sh**

TIPS:
Remember permissions, remeber that Ubuntu is CaSe SeNsItIvE.

:)

---

### Post by geirha on 2009-09-21
> **juancarlospaco said:**
> a bash script, the file extension of bash script is:
**.sh**


No. the .sh-extension is for sh-scripts. bash-scripts should preferably not have any extension at all, or if you insist on having an extension it should be .bash.

> **juancarlospaco said:**
> 
It need execution permission, so it can be executed.

Then make a launcher containing:

**sh /path/to/your/script/scriptname.sh**

That will execute the script with sh, NOT bash. The first line of a bash-script should read:
```
#!/bin/bash
```

Then, when you've made it executable, you simply use «/path/to/your/script/scriptname» in the Command-field when you create the launcher.

> 
TIPS:
Remember permissions, remeber that Ubuntu is CaSe SeNsItIvE.

:)

I do agree with that :)

---

### Post by z80 on 2009-09-26
so i just created a launcher and in the command area i  put the sudo mount command and it seems to work just fine though it does ask for the damn password every time i double click it, i also tried throwing one of these commands in the startup program list and it dosnt seem to do anything at all, it dosnt mount it and it never asks for the password to do so iether, so for the moment i have givin up on it auto mounting and will just double click the launcher on my desktop when i need access to the drive.

---

### Post by geirha on 2009-09-27
You can add an entry for that mount in /etc/fstab, allowing you to mount it with the mount-command, without needing sudo ... what does the mount-command look like?

---

