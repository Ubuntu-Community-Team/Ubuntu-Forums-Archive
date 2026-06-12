---
title: "Make CD Executable/Wine"
date: 2010-08-26
forum: General Help
---

### Post by fleamour on 2010-08-26
If this thread is true:

[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2010-January/010487.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2010-January/010487.html)

I cannot execute any CD software to install in Ubuntu.  

Is that correct?  Xubuntu has no such problems, is there a work around?

---

### Post by fleamour on 2010-08-26
Will try copying CD contents to /home then these instructions:

"Installing Windows Applications With Wine

To install Windows applications using Wine, follow these instructions:

Download the Windows application from any source (e.g. download.com). Download the .EXE (executable).
Place it in a convenient directory (e.g. the desktop, or home folder).
Open the terminal, and cd into the directory where the .EXE is located.
Type wine the-name-of-the-application.extension (e.g. wine realplayer.exe).
This will start the .EXE using Wine. If it is an installer, it should then run as it would in Windows. If the application asks for a directory to install the application to, select put it under C:\Program Files."

---

### Post by Vaphell on 2010-08-26
if your cd is in the drive, goto /media/cdrom and run wine setup.exe (or whatever)
```
cd /media/cdrom
wine setup.exe
```
this will go around the lack of executable bit on the setup.exe file which is in readonly mode and cannot be modified (it's a readonly cd after all). Executable bit defines what is allowed to run, not some arbitrary extension like .exe.

---

### Post by fleamour on 2010-08-26
Oh cool.  

I copied CD contents to /home directory then manually adjusted tick box permissions of all the executables.

Yours is a more elegant solution.

---

### Post by Vaphell on 2010-08-26
mark the thread as solved in thread tools, it will help other people to find answers

---

### Post by fleamour on 2010-08-26
> **Vaphell said:**
> mark the thread as solved in thread tools, it will help other people to find answers

Ah cool, must do that in future, never explored thread tools before, did not know it was there.

---

### Post by tiggsy on 2011-02-21
It won't work in Lucid on my laptop (which is with a friend while I try and fix his desktop)

---

### Post by Vaphell on 2011-02-21
what won't work? going to cdrom dir and running wine executable_file.exe from there?

---

### Post by tiggsy on 2011-02-21
going to /media/cdrom and running wine filename.exe still comes back that it's a non-executable file. even using sudo.

---

