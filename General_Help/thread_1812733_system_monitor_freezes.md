---
title: "system monitor freezes"
date: 2011-07-26
forum: General Help
---

### Post by amadis2009 on 2011-07-26
When I open gnome system monitor and try to click the processes tab, the window freezes. I can click on all the other tabs, but as soon as I click processes, the whole thing stops. What could have caused this and how do I fix it?

---

### Post by JC Cheloven on 2011-07-26
It's strange though. 
You can try opening a terminal and run ```
top
``` then open a second terminal and run ```
gnome-system-monitor
``` then play around with it until it freezes, and check the messages in the terminal and the processes at the top terminal. Perhaps this will give a clue.

---

### Post by amadis2009 on 2011-07-27
Not really sure what I should be looking for. I saw one zombie process pop up when I clicked on the processes tab and everything froze, but I have no idea which process it was or what to do with that info.

---

### Post by JC Cheloven on 2011-07-29
> **amadis2009 said:**
> Not really sure what I should be looking for. I saw one zombie process pop up when I clicked on the processes tab and everything froze, but I have no idea which process it was or what to do with that info.

What's the name of the process?
Does a warning or error message appear at the same time in the other terminal?
What happens if you kill that zombie prosess? To do that take a note of the process no. (PID), something as 1352, and at a terminal do "sudo kill 1352" (replace with the correct process no). Don't worry, in the worst case a reboot will get you to normal in case you kill something needed.

AKA "experiment a bit" :)

---

### Post by amadis2009 on 2011-07-29
I don't know which process is the zombie process. It just says someting like this:

Tasks: 185 total,   1 running, 183 sleeping,   0 stopped,   1 zombie
Cpu(s):  2.0%us,  1.3%sy,  0.3%ni, 96.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2059804k total,  1898980k used,   160824k free,    78188k buffers
Swap:  6037500k total,   106028k used,  5931472k free,   364956k cached

There's no indication of which process is causing problems.

---

### Post by JC Cheloven on 2011-07-30
To find out, bring the system to the state of window freezing (and zombie process appearing). Then open a terminal and```
ps ax
```
Search for the indicator "Z" (from "zombie") at the column named "STAT".

---

### Post by amadis2009 on 2011-07-30
Now I can see 2 zombie prcesses. One is the system monitor, the other is xdg-open. Can't kill xdg-open tho. Both of them listed as defunct. Not sure if that is helpful.

---

