---
title: "Won't load .exe"
date: 2010-07-10
forum: General Help
---

### Post by suckonthis300zx on 2010-07-10
I have ubuntu 10.04 and I want to load some programs to program my phone. I have wine and when i download (from a trusted source) an .exe file and right click and select open with wine something pops up and says, 
Blocked: wine start /unix
"The file '/home/cody/Downloads/MOTODEV.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit." 
How do i get this unblocked?

---

### Post by lisati on 2010-07-10
From the command line, the command is:
```
chmod +x {filename}
```
If you're using Gnome (the GUI) the relevant option is accessible by right-clicking on the file, and opening the "permissions" tab.

---

### Post by ankit singh on 2010-07-10
Right click on the file u have downloaded then go to properties->permissions tab,select the "allow executing files as program".

---

### Post by Rubi1200 on 2010-07-10
See here:

[https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required]("https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required")

In most cases, if you trust the source and are using WINE to run something (but not as root), all you have to do is right-click the file in question and under Permissions check the Allow execute file as program box. You should then be able to run it.

---

### Post by suckonthis300zx on 2010-07-10
thanks all... but do i have to do that to all programs? or can i just go to settings and make it where it will grant permission to all executable files?

---

### Post by ankit singh on 2010-07-11
Yes,its a security practice to install programs.

---

### Post by soldier1st on 2010-10-19
i have this same issue but only on 10.10 maverick meerkat. if the exe is not on the ubuntu drive the execute setting won't hold and changing any of the read and write permissions does the same. the workaround is to copy the affected exe to the ubuntu drive and set it as executible and the setting will hold but as soon as i restore the copied file to the non ubuntu drive the setting will not hold and yet on 10.04 it worked fine.

---

