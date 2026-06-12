---
title: "No launcher / taskbar after recent update! How do I get it back?"
date: 2011-08-25
forum: General Help
---

### Post by thacursedpie on 2011-08-25
Hi all!

A couple of days ago my install of Ubuntu 11.04 (I think that's the version I'm running) updated. When I later on rebooted my computer I was able to log in, but there was no taskbar / unity launcher, just my desktop screen.

I'm not really fluent when it comes to Linux, so I haven't got the faintest idea why this has happened and how I can fix it. Also, I don't know how I am supposed to open a browser / console without the launcher, so after this update my Ubuntu install is prety much useless...

Luckily I have a dual-boot with Windows 7 (using that to post this topic), but still, I want my Ubuntu to work :(.

Thanks in advance!

PS:
I searched around on the forums but wasn't able to find any relevant topics.

---

### Post by raja.genupula on 2011-08-25
in terminal do this 

```
ccsm
``` make sure that at desktop ubuntu unity box enabled .
 
if you didnt get it do this 




open  terminal  then give
```
 unity --reset
```

---

### Post by westie457 on 2011-08-25
From your Desktop press Ctrl+Alt+F1 to open a terminal. You will probably have to log in to use it.

Run the commands that raja.penupula has given then press Ctrl+Alt+F7 to return to your Desktop.

Everything should now be working.

---

### Post by thacursedpie on 2011-08-25
Okay, I first ran the 'ccsm' command, the tick-box was ticked.

After that I ran / am running 'unity --restart' , but that seems to be stuck at "Setting Update "run_key""... 

It also gave two errors:
"ERROR can't load plugin libunityshell.so!" 
"ERROR can't load plugin unityshell"

So atm it's not fixed yet. Thanks for the help so far.

---

### Post by raja.genupula on 2011-08-26
i said ```
unity --reset 
```
not restart 
give a try man .

---

