---
title: "What to do when system froze"
date: 2012-06-03
forum: General Help
---

### Post by mm6ff8 on 2012-06-03
I'm new to Ubuntu. Earlier today, after I downloaded a 1mb e-book in text format with Firefox's built-in downloader, Text Editor (gedit) came up and tried to load the document, then the whole system froze. The screen stayed there, mouse didn't work, keyboard didn't work apparently. I tried Ctrl+Alt+Delete, nothing. Before I force a power shutdown, I tried another method. I closed the lid of my laptop, and wait about 10 seconds, and open the lid, the login screen didn't show up as it should usually does, I pressed Power button, nothing, another try, the login screen showed up. After I log in, all other program and windows (2 Firefox with multi-tab in each, one Firefox Downloads windows, and one Home Folder) were still there but the text editor, it was as if I never double-clicked on the text file. I try the text file in FrReader and Firefox, it worked normally. I doubleclicked it to open with Text Editor again, it showed "Could not open the file /home/~/Documents/heian.txt."  Well, I'm going too far. My major concern is, when Ubunutu froze like that, is there any emergency keyboard combination in Ubuntu like the Ctrl+Alt+Del in Windows that I can get to a Process Manager to see what's frozen and to kill it?

---

### Post by miegiel on 2012-06-03
*gedit* doesn't handle large files well. If it's just for reading you might as well open the .txt file in *firefox*.

As a side note: Linux is sometimes unresponsive when it's really busy. It's not frozen, just really busy doing something you just told it to do. Just be patient, normally it's back faster than you can reboot.

---

### Post by layers on 2012-06-03
I remember once, a 5MB txt file took me about 15min to load.

Once, nothing worked, just the mouse and keyboard. So, usually you fire up terminal with Ctrl+Alt+T and type sudo reboot

---

### Post by mm6ff8 on 2012-06-05
I must have waited for over 1 minute and no patience. But, anything we can do to kill the process and terminating the waiting though?

---

### Post by Erden on 2012-06-05
> **mm6ff8 said:**
> But, anything we can do to kill the process and terminating the waiting though?

If the GUI is totally unresponsive, you can open a new terminal by ctrl+alt+F2 combination. F1 to F6 would work but F1 is mostly used for system messages.

After login 
```
top
```

Would bring the list of the processes. The process which causing the freeze more like to appears at top. For killing the process press 'k' it asks the process id (PID). Type the PID and for signal enter '9'. There are several signals; 9 is the harsh one. After killing the process press q to quit 'top' and ctrl+alt+f7 to go back to GUI.

Also for killing a specific process you can get the PID by 
```
ps aux | grep 'name of the application'
```

After getting the PID
```
sudo kill -9 PID
```
would kill the process.

---

