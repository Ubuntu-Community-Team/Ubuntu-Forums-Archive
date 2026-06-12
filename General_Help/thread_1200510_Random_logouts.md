---
title: "Random logouts"
date: 2009-06-30
forum: General Help
---

### Post by uru wolf on 2009-06-30
Hey guys, in the past few days my ubuntu (8.10 intrepid) has been randomly logging me out. It's the same as pressing ctrl+alt+backspace to kill the X server. It's only started happening the last few days, (When the weather has been much hotter, possible overheat?)

Does anyone know how I can take steps to fix this? I have looked around and there was an archived thread, but no solution. I could not find anything on google either.

---

### Post by XCan on 2009-06-30
Have you monitored your temperatures? Since you're only getting logged out and not rebooted, it feels like a GPU temp issue.

---

### Post by uru wolf on 2009-06-30
I have not, but will start if you think that a GPU overheat is causing it.

---

### Post by uru wolf on 2009-06-30
Um, any recommendations on programs to use? I have never had to monitor the temp before.

---

### Post by XCan on 2009-06-30
There are a lot of programs. Presonally I use lm-sensors with the sensors-applet to show my temperatures in the top bar of my PCs. Both programs are available in synaptics.

---

### Post by uru wolf on 2009-06-30
Woh! Just installed and enabled. GPU running at 67c, processors at 42-40
Think it might be overheating then?

---

### Post by XCan on 2009-06-30
67 C actually isn't bad for GPU and 42 C for CPU is good too. The question is if your cooling sometimes malfunctions, keep an eye on the temperatures for a few days and see if you see a temp spike next time you get booted.

---

### Post by uru wolf on 2009-06-30
Ok, will do. I have not had any restarts since posting. Only three this morning after about a 10/20 min cool down after being on for 24-ish hours. I will see if I notice anything that might cause it.

---

### Post by t0p on 2009-06-30
> **uru wolf said:**
> I could not find anything on google either.

That's interesting.  What  search terms did you use?

---

### Post by uru wolf on 2009-06-30
I searched for things like: "ubuntu ramdom logout" "random x( )server crashing" and things like that. There was plenty of stuff about crashing x servers but nothing that seemd to be related.

---

### Post by uru wolf on 2009-07-03
Ok, just had another random logout, the first one for a few days. The monitor says that the tempratures where at 50 (gpu) 38 and 36 for the processors. That's cooler than when I was getting the orrignal crashes.

I had open firefox, xchat and AMSN. But often use them togehter without any problem. I had just finished watching a youtube video. I have noticed that if I have lots of tabs open with flash content in it tends to slow firefox alot, maybe it's something to do with that?

---

### Post by XCan on 2009-07-03
Hmm, tough question. At least I believe we can rule out temperature issue. If you think it's a flash issue (possibly could be java issue as well) you should try and disable the addons in Firefox -> Tools -> Add-ons. I would tell you to look in the log files, but since I've no clue which one to look in, I'm going to leave that for someone else.

---

### Post by uru wolf on 2009-07-03
I am fairly sure it's not a java problem. Flash is the only thing that seems to slow firefox down. THe thing is though, the restarts do not happen regulary, and more often a few minuets after I log in, after the computer has been on for about 24 hours and had a 10-20 min cool down.

---

