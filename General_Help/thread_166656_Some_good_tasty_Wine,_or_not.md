---
title: "Some good tasty Wine, or not?"
date: 2006-04-26
forum: General Help
---

### Post by sinkxdie on 2006-04-26
Ok, so I'm having fun enjoying my Wine, when all of a sudden I come accross this. it's pretty obvious what program I was trying to run. :D

```
sinkxdie@ubuntu:~$ wine "c:\program files\itunes\itunes.exe"
err:module:import_dll Library USERENV.dll (which is needed by L"C:\\program files\\itunes\\itunes.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\program files\\itunes\\itunes.exe" failed, status c0000135
sinkxdie@ubuntu:~$

```

What do I do?

---

### Post by bluevoodoo1 on 2006-04-26
If you have itunes installed on windows you can try to see if you have the necessary USERENV.dll file on windows and copy it over to Ubuntu.

---

### Post by sinkxdie on 2006-04-26
If I find it, would I just copy it into the itunes directory?

---

### Post by sinkxdie on 2006-04-26
Ok, well now I need to get quicktime, which will probably be easy to. But thank you so much, I dont know how stupid I must be to not even think of that. :D

EDIT: Its not easy. I put the whole program files directory into my .wine program files and it's still saying, "Quicktime was not found"

---

### Post by bluevoodoo1 on 2006-04-26
[QUOTE=sinkxdie]Ok, well now I need to get quicktime, which will probably be easy to. But thank you so much, I dont know how stupid I must be to not even think of that. :D[/QUOTE]

Nah, I only know of it because someone told me that when I was in a similar situation. I hope you get it up and running!

---

### Post by sinkxdie on 2006-04-26
Should I just run the itunes installer file and install it to my "wine" computer?

---

### Post by sinkxdie on 2006-04-26
Right now its installing, I only encountered one error, but the installer just continued as normal. :D I love itunes...wonder if it will be able to recongize my iPod?

---

### Post by bluevoodoo1 on 2006-04-26
(Hmmm, I haven't tried putting itunes on ubuntu, so I hope someone will chime in. with more ideas. Installing it with the itunes installer to your wine computer--as you said--should/might work.)

---

### Post by sinkxdie on 2006-04-26
It keeps repeating the "installing quicktime" step with the progress bar filling up and then restarting.

---

