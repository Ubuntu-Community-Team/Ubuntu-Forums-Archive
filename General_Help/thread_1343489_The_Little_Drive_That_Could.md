---
title: "The Little Drive That Could"
date: 2009-12-01
forum: General Help
---

### Post by Xog on 2009-12-01
Hello all,

It all started with my undying urge to re-watch the Ruroni Kenshin anime series. Off to torrentland to get the series. Within a minute or so I'm downloading episodes 1-95, plus the 1-5 OVAs. After a couple days I noticed significant performance issues with my laptop upon booting, general display issues such as screen flashing, unexplained program stoppage (including the OS itself) and complete instant system shutdowns. Eventually, throughout the week, ubuntu's hard drive surveillance program "Palimpsest Disk Utility" (System => Admin => Disk Utility) notified me about my hard drive failing. At first it said I had 160 Bad Sectors, but the system passed its performance test. Over the next following days, more and more bad sectors started appearing. Currently I have 655 Bad Sectors, and "Disk Failure is Imminent." I hope I can finish this post before it dies. It's been a few days since it started saying that.

So, as my hard drive problems get worse and worse, I continually try to finish the series before my HD goes capoot. I'm expecting to receive a new one for christmas from my wife, I keep involving her in my torment, suffrage, and turmoil of the failing beast of past. This HD is from 2004, 120GB and has an active, powered-on life of 1.8 years. I've known ye well.

Discussion:

1) Any takers on how long it takes for the drive to stop working all together?
Vote:
a) 1-3 days
b) 4-6 days
c) 1-2 weeks
d) 3 weeks to a month

--

2) Anyone know if ubuntu would be some kind of cause for HD failure? I've read recently that "9.10 has been ripping up several hard drives" and it wasn't more than a few weeks that I installed ubuntu on this HD. It was windows before.
 
--

3) Would you reinstall 9.10 if you've recently had your HD fail shortly after installing it the first time?

---

### Post by openuniverse on 2009-12-01
.

---

### Post by Xog on 2009-12-01
> **openuniverse said:**
> hopefully i won't be accused of spreading fud, but there was an issue "in the days of gutsy" that caused a stir. it was helping to kill a drive on an old laptop, but this was a laptop i was planning to use strictly for a livecd, so i didn't care. in fact before it "died" it was the laptop that helped me get rid of windows forever and switch from xp to xubuntu. (thanks, gutsy guys and gals.)

the problem has been slow to resolve or unresolved (it's been another year, must look at launchpad) partly because it's NOT ACTUALLY UBUNTU to blame. it's really more of a bios/apm issue, it tries to spin down way too often for reason. also let me point out that it can also happen in windows, but windows spends so much time accessing swap ;) and other things that it may be less of a problem for a lot of windows users.

the "solution" (hack) was to set drive apm (using hdparm) to 254 or 255... but be warned, this comes with its own hazards, especially for laptop users. also it doesn't work for everyone. debian "patched" this early, using the same hack! for other people it can result in drives running with higher temps, one of the possible side effects of the "fix." i used to run smartctl to monitor both load_cycle_count and temp, stopping the problem on my best machine.

i'm still having the problem in 9.10 on a friend's laptop, but before you tsk, it's worse in his windows setup (there is a port of smartctl for windows, too. it even uses gnu/linux naming, like /dev/sda1...) and the hdparm setting helps but doesn't stop it completely. **one of the heroes of that debacle was ubuntu-demon, who i've seen in a recent thread. he probably knows more about this. but you know? no one knows.** if they ever get solid-state to handle as many writes as their electro-mechanical cousins, this will be a non-issue. until then, for me at least, it's a mystery... but nothing you can't monitor with palimpsest. (thanks for pointing that out btw, it's very nice!) **edit:** by the way, there's no telling if it's a) b) c) or d). it sounds like you're progressing from a) to c), but at any rate, probably non-linear. hope this message reaches you well.


Well thanks for the information. Have you ever experienced any hard drive issues of the sort?

Also I'd also like to announce that just a few moments ago, firefox crashed. So I went to go open it from the panel, but right as I clicked, Poof! The panel disappeared. So I went to the bottom panel, right clicked an Poof! Gone! I right click on my desktop and Poof! Blackness! Computer completely off. I feel like Elminster! :lolflag:

edit: but it started back up and all is OK for now..

---

### Post by openuniverse on 2009-12-01
.

---

### Post by Xog on 2009-12-01
> **openuniverse said:**
> yes, on the machine i installed 7.10 on. (back when the 7.10 repos were still active.) i think it already had some issues pre-ubuntu, but the load_cycle_count was screaming forward, and i had to get rid of ubuntu and put dsl (uses less of the drive) on it. the dsl install didn't last long, either, but running dsl toram (oh, i wish there was a flavor of ubuntu that did that in 512m of ram...) made the install unnecessary.

What signs of hardware failure were you receiving? Anything unique and of interest?

---

### Post by openuniverse on 2009-12-02
.

---

