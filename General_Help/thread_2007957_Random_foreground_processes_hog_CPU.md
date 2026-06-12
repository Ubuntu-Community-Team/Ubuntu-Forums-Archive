---
title: "Random foreground processes hog CPU"
date: 2012-06-21
forum: General Help
---

### Post by SwimDude0614 on 2012-06-21
Hello,

I've been having this problem for over a month now and have re-installed 3 times. It keeps coming back. It first happened with 10.04 64-bit, and I decided it was a good excuse to upgrade to 12.04 64-bit (did a fresh install). Since then, I've had the same problem and reinstalled from scratch twice.

Problem:
Ubuntu randomly starts slowing down a lot. I open a terminal (wait 1 minute), type "top" (wait 30 seconds), and then watch what is hogging my CPU, hoping that if I kill it my problem will be solved. What do I see? EVERYTHING is killing my CPU. Any running application.

For instance, right now as I type this, thunderbird-bin is using 46%. Now Chromium is using 20%. Oh look... psensor of all things is using 20%. And now empathy at 56%. Scatch that... 86%.

If I close any of these apps, the others will pick up the slack. Thunderbird is usually the last app I close and I'll regularly see thunderbird-bin using 80-90% with the other 10-20% used by Xorg & and compiz.

Hardware:
Dell E6400 laptop
Core 2 Duo P8400 @ 2.26 GHz
4 GB DDR2
NVidia NVS 140 w/ 512 MB
Dell 27" monitor @ 2560x1440

Any help is appreciated. This is my work computer having the problem and it is *severely* affecting my ability to meet deadlines.

David

---

### Post by Redblade20XX on 2012-06-21
Has this always happened ever since you first started using linux or is this just a recent thing?

Can you check how much memory is being used and post?
```
free -m
```

Do you have any seperate partitions such as a /home partition which is seperate from the root?

If so, maybe some configuration files got carried over.

-Red

---

### Post by SwimDude0614 on 2012-06-21
This happens every once in a while. I was fine for the first 5 hours of my workday, and then it just hit half an ago (it's taken that long to collect the data). Eventually it goes away - this is usually the point where I just go home for the day and leave the computer on all night. It's fine by morning. If I reboot, it doesn't help. I have to just let it run for idk how long... but all night has always fixed it.

I've closed all the windows already so perhaps the results of "free -m" are skewed. It's still acting very slow though.

Mem:
total   - 3943
used    - 2581
free    - 1361
shared  - 0
buffers - 160
cached  - 929

Swap:
total - 4082
used  - 122
free  - 3960

Before I killed everything, I took a screenshot of top. Here it is.
-Edit-
I just added up the CPU usage visible from this screenshot. Comes out to 196% - both cores fully thrashed.

---

### Post by SwimDude0614 on 2012-06-21
> **Redblade20XX said:**
> 
Do you have any seperate partitions such as a /home partition which is seperate from the root?

If so, maybe some configuration files got carried over.

-Red

No separate partitions. I carry some files over, like documents and .vimrc, but I don't *think * anything that should be affecting this.

---

### Post by SwimDude0614 on 2012-06-21
It finally brought itself back to normal. It took ~45 minutes this time. Here's another snapshot of top to compare to when nothing is running (except Thunderbird, psensor, top, and screenshot).

---

### Post by QIII on 2012-06-21
Does this behavior occur in a live session?

---

### Post by SwimDude0614 on 2012-06-21
Not sure. I'll boot one up now and run for a while.

I guess that would tell me if it's the hardware???

---

### Post by QIII on 2012-06-21
A clue, but not definitive.  

Did you check the md5sum on your ISO download?

---

### Post by vasa1 on 2012-06-21
> **SwimDude0614 said:**
> ...
Mem:
total   - 3943
used    - 2581
free    - 1361
shared  - 0
buffers - 160
cached  - 929

Swap:
total - 4082
**used  - 122**
free  - 3960
....
Interesting that with 4 GB RAM, **swap** is being used. Is swap being used a lot? Perhaps you could log swap usage over time?
And why the two zombies?

---

### Post by SwimDude0614 on 2012-06-22
md5sum is correct

I don't know what zombie processes are, therefore I don't know why they're there.

I've never noticed swap being used much. I don't think it is. I do run a LOT of stuff at once. I think at the time I was running thunderbird, eclipse, empathy (2 chat windows), chrome ~8 tabs, psensor, clusterssh and various terminal windows. I've done this many times though, and there is no one program or last straw that makes the computer act slow. I'll be in the middle of typing in Eclipse or browsing a web page or writing an email, and the whole thing instantly slows down 10 fold. The cursor stops moving (lags), the webpage stops loading, etc.

I'm booting up the Live Disk now to check that. Got too hungry last night to continue working.

---

### Post by SwimDude0614 on 2012-06-22
Live disk is having issues now.

Ubuntu 12.04 64-bit on a 2048 MB fat32 HDD partition without persistent storage. laptop specs are the same in the post above.

I've switched mirrors to mirror.cs.umn.edu (I get incredible speeds from this mirror where I am).

Installed after boot-up:
gimp
chromium-browser
vim
exuberant-ctags
psensor

Running at the time of swampage:
psensor
empathy w/ 3 protocols, no chat windows
top
two idle terminals
thunderbird with one email account added
chromium with 1 static html tab

Attached are some screenshots of what's happening (i hope they're helpful... they take forever to get when the problem is occurring lol). I've taken 4 total, one each from top and psensor from before and after it got bogged down. In the graph, you can clearly see when it started happening - CPU usage jump significantly, but does hit the ceiling. Then CPU jump again and is slammed against the ceiling constantly. This is where I'm stuck now.

---

### Post by SwimDude0614 on 2012-06-22
co-worker thinking heat issue... will get back shortly

---

### Post by QIII on 2012-06-22
Heat issue may be a symptom rather than a cause.  Runaway processes heat up the hardware.

---

### Post by Redblade20XX on 2012-06-22
Somethings telling me this might be a graphics card problem.....
What driver do you have installed the open source one or the proprietary one?

-Red

---

### Post by jeanfi on 2012-07-06
psensor should not take so much cpu (15/20%) except maybe few milliseconds during startup or when the graph window is hidden and you request to show it back.
One of my laptop (precision M4300) is quite similar to your laptop and I did not notice any issue.

I can see in the top screenshot that the xorg/compiz processes cpu usage is very high. Is it the case only when psensor is running? Your issue seems more related to video support or unity/WM.

---

### Post by Beatsleigher on 2012-07-06
Hmm... I have something similar, but I've kind of gotten used to it, because of WIndows...

It's just processes, that are runnung, but don't know what to do, so they "think" of something to do, and by doing this, they use up all the CPU. 

How many of you are using and Android? Well, every single one of you (Doesn't matter, whether  you are rooted or not, or using a CROM) will get this feeling, when they use an app, but don't need it anymore and just go to the home screen. 

The app get's told to close down, and cache itself up, some apps can't do that at that exact moment, so they finish their process, and "forget" what they were asked to do, so they sit there, get bored and muck around... If you force close them, however, or reopen and close them,, it goes away... that's what I'm guessing is going on in our laptops/computers...

To the problem with the SWAP, try checking, if your BIOS is set do do some random checks... That sometimes is enabled, b default on Dell computers, to ensure maximum durability... And it sucks a hell of a load of RAM, this RAM sucktion cannot be recognized by OSs

---

