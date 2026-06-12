---
title: "Matlab issue"
date: 2011-09-15
forum: General Help
---

### Post by Failican on 2011-09-15
Hey

I have recently installed matlab on my ubuntu computer.. I've red most of the threads here on how to get it to start, but it didnt help..

I have installed it on another partition, the path is: media/D:/Matlab/

I tried to copy it to an external hdd and when i start it in it with /.matlab it works but not on the computer it self.

I tried the chown -R ${USER}:{USER} ~/matlab
But after that I got the error msg: 850: Can't open //bin/util/arch.sh

After that it doesnt start off in the external hdd ether:( 

I've tried to change the matlab file with gedit as some people suggested but it wont work.. 

ps. the reason why i didnt install it on / is because its no space left.. 



thanks!

---

### Post by Ceiber Boy on 2011-09-15
From memory (because the last time I used MatLab was in University a number of years ago) their is only releases for Windows and Mac. therefore i assume you are trying to run a windows version under Wine?

Assuming you are using wine, not all windows programs will run nicely with it. I also have a feeling that MatLab defaults to wanting to be on the C: drive, if it is not located there it may take issue with you.

I've had issue with trying to run scientific programs under Linux that have been designed for windows, If you have a spare copy of windows laying around (nothing special even XP would do the trick) run it in visualization (Virtual Box) then install MatLab on that, at least it will be happy as its running in its native environment.

In any case it sounds like you need to make some room on your HDD.

Good Luck.

---

### Post by tomkat3 on 2011-09-15
If you don't need Matlab's graphical tools, you should use Octave. Its exactly the same except its all command line and runs from terminal. It reads .m files just like the full version. Just type in 'octave' into a terminal and ubuntu should tell you how to get it.

What you can try is to go into your windows partition, copy/paste the MATLAB folder in the program files into your Ubuntu partition, then use wine to start the matlab.exe or whatever executable matlab starts with. Mine uses 

```
MATLAB\R2010a\bin\matlab.exe
```

I did this a few weeks ago, and I was able to get to the activation wizard, but I couldn't find my license number on my university, so I stopped. Its been on my to do list for awhile... I'll try it out again if I can find the time. Copying the Program Files folder like this worked for some windows games I was trying to run on ubuntu.

I hope that was useful!

---

### Post by Failican on 2011-09-16
Yeh I'm using octave now but want to get matlab, because its free from the university, and no its a linux version of matlab..

---

### Post by Failican on 2011-09-17
So no one knows how to get it to work? because i really need the graphics from matlab, since I will have a test in matlab later and then it would be stupid to train in octave


thx Failican

---

### Post by Ceiber Boy on 2011-09-18
> **Failican said:**
> So no one knows how to get it to work? because i really need the graphics from matlab, since I will have a test in matlab later and then it would be stupid to train in octave


thx Failican

I can't imagine it requiring anything special (in terms of installation process) as commercial software tries to make it as easy as possible for the end user to install and use. So their might be some clues in looking at the install process.

---

