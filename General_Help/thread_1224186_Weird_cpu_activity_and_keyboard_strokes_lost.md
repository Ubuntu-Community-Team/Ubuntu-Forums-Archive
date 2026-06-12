---
title: "Weird cpu activity and keyboard strokes lost"
date: 2009-07-27
forum: General Help
---

### Post by triplemaya on 2009-07-27
From time to time I lose keystrokes. When this starts it makes the system unusable, and I have to reboot to solve the problem. I notice that the cpu usage is very high, 30 - 40 percent, but when I look in System Monitor all the processes are sleeping - except System Monitor of course! It's core two duo so the system should not be struggling just to run the os. I've tried closing all apps and restarting my open office window, but the problem is still there. I usually only run Firefox and Thunderbird along with open office, so nothing else is going, or at least should be going on, apart from standard system activity. Please can someone tell me what to look for and how to go about solving this problem. Thanks.

---

### Post by aesis05401 on 2009-07-27
Next time it happens try opening a terminal and typing 
```

sudo top

```

This may show a slightly different list of processes - at least it has for me in the past. 

Also, I had a similar issue with my machine after it would wake up from hibernation.  Do you experience this issue after fresh boots?

---

### Post by triplemaya on 2009-07-27
Hi. Thanks, I'll try that. And no, after a fresh boot it always works ok for a while. Sometimes it's ok all day, sometimes it goes bad quite quickly, and then happens again quite soon after a reboot. I've been starting to wonder if it is something connected to firefox having a web page open which causes the problem - I have it so that firefox open on boot up, and since I often have a lot of windows open, but the windows do of course change from time to time, I wondered if it was that. But the problem goes on even after I shut down firefox, so that didn't seem likely, but it is the only thing I can think of which really varies in the use of the computer.

---

### Post by aesis05401 on 2009-07-27
One other thing occurs to me - When I used to run the standard gnash plugin for firefox it would sometimes cause what you describe. 

FF/Tools/Add-ons/Plug-ins...  Gnash is listed as Shockwave - but says gnash in the description.  If you have that enabled, try disabling it next time. 

When it is running, it appears as 'gtk-gnash' in process lists (I think).

---

### Post by triplemaya on 2009-07-27
Ok, thanks. It's not doing it at the moment, but I have all the same processes running as I had last time I had the problem. And the cpu usage is still weirdly high, one cpu 20ish and the other 40ish, swapping around between the two - presumbably normal - and a spike to 60 or 80 from time to time.

---

