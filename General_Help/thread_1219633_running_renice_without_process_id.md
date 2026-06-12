---
title: "running renice without process id"
date: 2009-07-22
forum: General Help
---

### Post by RedWagon on 2009-07-22
I'm running TF2 in Wine and was having a problem with wineserver taking up lots of CPU and lagging my game every couple minutes.  Running ```
sudo renice -20 -p 28624
``` or whatever the hl2.exe process ide is fixes this, though it's kind of annoying to open a terminal window, look up the process id and run this every time I launch the game.  I'm looking for some way to automate this.
I read up on renice but couldn't find a way to do somehting like renice -20 hl2.exe
I was wondering if there was something I was missing, or if I could create a script that would get the process id somehow

list processes | grep hl2.exe
remove everything but the process id, store to variable
renice -20 -p variable

---

### Post by kidders on 2009-07-23
Hi there,

> **RedWagon said:**
> it's kind of annoying to open a terminal window, look up the process id and run this every time I launch the game.You can renice processes by name with something like ...```
# renice -1 `pidof apache2`
17858: old priority 0, new priority -1
13806: old priority 0, new priority -1
13805: old priority 0, new priority -1
13804: old priority 0, new priority -1
13803: old priority 0, new priority -1
13802: old priority 0, new priority -1
13801: old priority 0, new priority -1
13797: old priority 0, new priority -1

```

Unfortunately, process names are not always unique enough ... for example, suppose you wanted to select a process based on one of its arguments. One way to do this is pretty much what you suggested ...```
# ps axo "%p %c %a" | grep hl2.exe | cut -d" " -f1 | xargs renice -20
```[LIST]
[*]**ps axo "%p %c %a"** - Reformat the usual output of ps to cut out trash that you don't need, and put the PIDs in a predictable position.
[*]**grep hl2.exe** - Filter the output.
[*]**cut -d" " -f1** - Extract the first field of the filtered process list (which will always be the PIDs).
[*]**xargs renice -20** - Construct & execute a "renice" command out of each PID.
[/LIST]

That command is pretty long-winded, so you could make your life easier by throwing together a small script to launch & renice your application in one step ...```
#!/bin/bash
/path/to/app/here &
sleep 4
ps axo ...
```Some notes:[LIST]
[*]The '&' after the command to launch your app is important. Most processes do not release control of a terminal until they're finished running, so you'll want to force your app into the background to allow the script to continue running.
[*]The "sleep" command is also a requirement. Without it, the process selection could sometimes take place before your system has had a chance to launch your app. Sleeping for a long time (eg 4 to 8 seconds) would give your app plenty of time to spawn any child processes you may want to renice.
[*]You could save the script into /usr/local/bin and stick a shortcut to it on your desktop. In case you don't know, anything in /usr/local/bin should be owned by root and be "chmod"-ed to 755 (ie read/execute permission for everyone).
[/LIST]

Anyhow, I hope that helps.

One caveat I should mention is that giving user processes a priority of -20 can cause damaging instability ... even the small step down to -19 would be infinitely more preferable. Basically, you don't want a situation to arise where your game is granted priority over something your system *needs* to do in order to keep running. For example, should your game hang, or become unstable, you may find yourself unable to terminate it, and could wind up corrupting your filesystems or overheating your box!

---

### Post by RedWagon on 2009-07-26
Thanks for the awesome response, that was exactly what I was looking for.  I love how there are multiple ways to do almost everything in Linux.
I'm adjusting Steam.exe and hl2.exe and it's impossible to run two copies of either at the same time so the first method works fine.  
> giving user processes a priority of -20 can cause damaging instability
I have a quad core system so I figured this wouldn't be a problem, however I have had two occasions when playing TF2 that my screen just instantly froze up and turned different colors which I attributed to hardware errors, but thinking about it it could have been caused by hl2 running at -20.  I set my tf2 script up for -19 so hopefully that won't happen again.  
Anyways, thanks again!

---

