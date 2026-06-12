---
title: "good linux based SETI@HOME style screensavers?"
date: 2009-11-05
forum: General Help
---

### Post by Arminius on 2009-11-05
anyone know ones that are good for linux? not interested in that actual SETI@HOME cause I don't think they will ever find anything.

can't google them cause I don't know what they would be called.

---

### Post by mike998 on 2009-11-05
Electric sheep is pretty.
Distributed Screen saver...

---

### Post by Arminius on 2009-11-05
that's nice but was wanting to actually run a screensaver that contributes to science.

---

### Post by doas777 on 2009-11-05
well you can run boinc with seti, or folding, or climate change, or einstein's gravity waves, or whatever, but last time I checked, the linux version did not run a screensaver. it just runs invisibly in the background.

I used to run a number of boinc projects, but lately, I'm concerned about the power cost from gunning my CPU at 100% 24 hours a day.

---

### Post by Arminius on 2009-11-05
that's fine, doesn't have to be a screensaver
I found this BOINC manager
it's not very well organized though, the website got me keen on the clean energy project. but can't find it anywhere in the lists.
anyway I've settled for Einstein@home, thanks for your help

---

### Post by tom.swartz07 on 2009-11-05
you could try folding at home.

it uses the cpu to analyze protein folds.

---

### Post by Arminius on 2009-11-05
why is it I tell BOINC manager to only do it's think if the computer is idel for 5 mins, and it just ignores me, my processor is %100 all the time, it only stops if I manually tell it to? was hoping it would kick in when there are no mouse movements or keystrokes, and shut itself down when I come back.

---

### Post by ST3ALTHPSYCH0 on 2009-11-05
Just a thought, but you might want to run Prime 95 (I don't remember the name of the linux version) for 24 hours before contributing to such a project. Even totally stock systems can have instability, and you wouldn't want to contribute faulty calculations to a project you're trying to support.

---

### Post by Arminius on 2009-11-05
did u mean primegrid? can't see prime95 in the list, and why them? not seeing how I can prevent faulty calculations, only followed the install instructions.

seems to be running fine

ok, I'll stop running milkyway@home and do primegrid for a bit.

---

### Post by ST3ALTHPSYCH0 on 2009-11-05
The Linux version of Prime95 is called Mprime. What this will do is put an immense amount of stress on your CPU (much as the CPU intensive work of above mentioned projects) and if it fails prime before 24 hours then you could be looking at giving the project you're supporting faulty calculations. If they were to base other calculations on the results of yours then the rsult would be further and further from correct.
[Here's]("http://en.wikipedia.org/wiki/Prime95") the wiki about Prime.

You'll want to run the torture test for 24 hours (unfortunately you'll need to just let it run). The last time I ran it with instability I made it 18 hours before fail, that's why I suggest 24.

---

### Post by wildweathel on 2009-11-05
Arminius, you want to keep distributed computing programs from interfering with other programs, right?  On Windows, you'd do that by only running them when the screensaver runs.  On Unix-like systems, you tell the scheduler to give them a very low priority.  If you do that, you don't have to shut them down when you're using your computer; Linux will keep them out of the way.   This is called making a program "nice," because the "nice" and "renice" commands are the original ones for setting it.

Computing tasks that move a large amount of data can still cause noticeable performance issues even when niced.  (They're not supposed to, but Linux isn't perfect)  CPU-bound ones are no problem, though.

To nice a task, run nice -n *niceness program*.  For example, I just started mprime with "nice -n 20 mprime," and it's running as I'm typing this.  "man nice" will give more information.

I imagine BOINC has option to set niceness, but I've never run it, so I don't know.

---

### Post by Arminius on 2009-11-06
nah I couldn't get this mprime to work, I'm running BOINC exactly as the instructions say, it's upto them to design it to not send bad data, it's also upto them to filter out programs that are messing up.

---

### Post by XCan on 2009-11-06
> **Arminius said:**
> why is it I tell BOINC manager to only do it's think if the computer is idel for 5 mins, and it just ignores me, my processor is %100 all the time, it only stops if I manually tell it to? was hoping it would kick in when there are no mouse movements or keystrokes, and shut itself down when I come back.

On my computer, boincmgr totally ignores my mouse movements and clicks. However, it appears that keyboard strokes work fine. But it appears it doesn't even stop for you on keystrokes. A question though, which boinc manager version are you running? I think the one in Karmic doesn't idle the GPU for such projects supporting it.

---

### Post by Arminius on 2009-11-07
I have a dual core, and it's only using one core
how do I tell it to use both?

---

### Post by doas777 on 2009-11-07
all your preferences for boinc are stored in your project profile online. login to your account on the project server and edit your preferences there. at least thats the way it works for windows.

---

### Post by Arminius on 2009-11-09
I read that a whole lot of networked PS3's broke a record for calculations done.

I have 1 ps3, is it possible to crunch numbers on that when I'm not using it?

---

### Post by doas777 on 2009-11-09
I have to assume that they have installed another os on their PS3 (ubuntu could be installed on older ps3's). so if you have modded the os, I guess you could.

---

