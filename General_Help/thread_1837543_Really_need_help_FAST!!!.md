---
title: "Really need help FAST!!!"
date: 2011-09-01
forum: General Help
---

### Post by zaidhorse on 2011-09-01
I am new to linux/ubuntu. I really got used to ubuntu 10.10 and compiz but in natty 11.04 when i tried to apply 3d effects through compiz it gave me a whole load of warnings and when it applied I lost the whole unity interface! I can't even see the the exit, minimize, and maximize buttons in he windows. I don't have the launcher dock nor the panel at the top. None of he default ubuntu shortcuts work and I can't open terminal. Is there a way to restore Ubuntu back to the moment before I started messing with compiz? I would really hate to reinstall ubuntu. Please help me!!!:(:(:(:(:mad::mad::mad::mad:

---

### Post by elliotn on 2011-09-01
reboot your system then open terminal and do

compiz --replace

---

### Post by squenson on 2011-09-02
> **loekanle said:**
> I need help too , my ClamTk virus scanner has no menu options like file, view , option and etc

and the antivirus engine and GUI version has a stop sign instead of a check mark   

Help!!!!!!!!!!
Please open a separate thread for your own problem, it has nothing to do with the OP's one and you just create confusion!

---

### Post by alphacrucis2 on 2011-09-02
```
unity --reset
```

Log out and back in.

---

### Post by zaidhorse on 2011-09-02
> **elliotn said:**
> reboot your system then open terminal and do

compiz --replace

Ok that sounds good but i have no access to the terminal. I only can see and use the icons on my screen and I don't have one for the terminal. Also the keyboard shortcut to open the terminal doesn't work.

---

### Post by Wim Sturkenboom on 2011-09-02
<ctrl><alt><Fn> (n is 1..6) should get you to a console
try the above commands
<ctrl><alt><F7> (sometimes <F8>) get you back to GUI

Failing that, start in recovery mode (I hope Natty still has that), drop to root shell and try the above commands

Note that this is only to get you to some kind of terminal; I don't know anything about the solving your problem.

PS Why do you need help fast?

---

### Post by zaidhorse on 2011-09-02
> **Wim Sturkenboom said:**
> <ctrl><alt><Fn> (n is 1..6) should get you to a console
try the above commands
<ctrl><alt><F7> (sometimes <F8>) get you back to GUI

Failing that, start in recovery mode (I hope Natty still has that), drop to root shell and try the above commands

Note that this is only to get you to some kind of terminal; I don't know anything about the solving your problem.

PS Why do you need help fast?
  Thanks for your help. I am a programmer and all of my programs and settings are on this machine
ok in both the recovery and the ctrl atl and fn methods when i try compiz --replace the terminal replies "compiz (core) -Fatal: Couldn't open display"

---

### Post by zaidhorse on 2011-09-02
the unity --restore command did something but didn't bring back the ui

---

### Post by zaidhorse on 2011-09-04
Why isn't any one helping anymore? Please the compiz and unity commands that you guys gave me earlierr didn't do anything

---

### Post by fidelandche on 2011-09-04
I had the same problem, before I reset Unity, I entered this command first 

sudo apt-get install ubuntu-desktop

then followed by

unity --rest

and then I let unity -- reset run for thee minutes before closing the terminal and then rebooting and it all worked fine.

Cheers

Andy

---

### Post by zaidhorse on 2011-09-04
> **fidelandche said:**
> I had the same problem, before I reset Unity, I entered this command first 

sudo apt-get install ubuntu-desktop

then followed by

unity --rest

and then I let unity -- reset run for thee minutes before closing the terminal and then rebooting and it all worked fine.

Cheers

Andy
 
ok thanks.

---

