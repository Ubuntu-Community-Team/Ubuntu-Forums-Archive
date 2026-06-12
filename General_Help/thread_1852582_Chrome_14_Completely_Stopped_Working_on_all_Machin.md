---
title: "Chrome 14 Completely Stopped Working on all Machines"
date: 2011-09-30
forum: General Help
---

### Post by teejay17 on 2011-09-30
Something really strange happened today: Chrome 14 on all my Ubuntu machines (and one Linux Mint) stopped working. Chrome just freezes solid on startup. 
This is affecting one 11.04 Ubuntu machine, one Linux Mint 11 machine, and 3 test boxes running 11.10. 
This is not affecting my Windows machines, however. 
I thought it may have been due to updates, so I did not update one test box running 11.10 where Chrome was fine yesterday. Chrome still freezes solid on opening -- I can't access the wrench button or anything. 
What could possibly be causing this?

---

### Post by CHEWS on 2011-09-30
I noticed that chrome freezes on multiple monitor setup (at least on nvidia proprietary driver), no clue why. if your on multi monitors try disabling though doesn't sound like you are. try sudo apt-get install -f and tell me if that fixes it if not I will try and help. And are you using official chrome or the chromium browser?

---

### Post by teejay17 on 2011-09-30
> **CHEWS said:**
> I noticed that chrome freezes on multiple monitor setup (at least on nvidia proprietary driver), no clue why. if your on multi monitors try disabling though doesn't sound like you are. try sudo apt-get install -f and tell me if that fixes it if not I will try and help. And are you using official chrome or the chromium browser?
No, it isn't a multiple monitor set up. 
sudo apt-get install -f  got me 0 installed, 0 upgraded... and Chrome still froze when I tried to open it. 
I am using official Chrome, the most recent version (after the Flash fix) .186 or around there. 
The weirdest part is that it was fine yesterday... and it just started to freeze on all machines today. 
I wonder if this has something to do with browser syncing? Maybe something in the browser syncing for Linux is messed up, but okay for Windows.

---

### Post by CHEWS on 2011-09-30
if you create a new user and run chrome from that does that chrome work? Not as an actual work around but to help trouble shoot potential causes. if it works in other users a have a few ideas to try and fix it.

---

### Post by Gatemaze on 2011-09-30
if you run chrome from terminal are there any error messages?

---

### Post by CHEWS on 2011-09-30
that was my next suggestion if the other user didn't work and if it did it still involved terminal lol

---

### Post by teejay17 on 2011-09-30
I backed up/changed the name of my user profile and Chrome now doesn't freeze. 
```
~/.config/google-chrome/Default
```This is the second time I've had to do this within the last couple months; something is not working right with the browser sync. 
Now I will see if I can re-sync without crashing...fingers crossed...

---

### Post by teejay17 on 2011-09-30
> **teejay17 said:**
> I backed up/changed the name of my user profile and Chrome now doesn't freeze. 
```
~/.config/google-chrome/Default
```This is the second time I've had to do this within the last couple months; something is not working right with the browser sync. 
How I will see if I can re-sync without crashing...fingers crossed...

Well, Chrome is is now working and syncing on my main Linux machine, and that's important. Now it looks like I have to change my profile on all the rest of my Ubuntu/Mint boxes. :(
I still find it odd that Chrome was syncing on all my Windows machines no problem, but was not syncing/freezing solid on Linux. I wonder if there may be an issue in there somewhere...like a bug perhaps.

---

