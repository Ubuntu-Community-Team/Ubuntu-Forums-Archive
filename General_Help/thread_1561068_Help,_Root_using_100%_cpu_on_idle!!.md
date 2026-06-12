---
title: "Help, Root using 100% cpu on idle!!"
date: 2010-08-25
forum: General Help
---

### Post by fatriff on 2010-08-25
Hi there, I've got 10.04 running and I just couldn't believe how slow it was, even playing a simple youtube video is jumpy, compared to xp on the same machine, this is 3 times slower..

A quick look at top tells me root has 100% cpu at all times. Nothing is running.

Any ideas what is going on?

[IMG]http://dl.dropbox.com/u/2528687/Screenshot.png[/IMG]

---

### Post by inameiname on 2010-08-25
Does this continue after a restart of your computer?

Also, what is that terminal command you put in to get that readout? I usually just use gnome-system-monitor.

---

### Post by fatriff on 2010-08-25
I just type the word top,

Yes it continues regardless of what I do, even starting without saving any of the previous running programs. I had dropbox running and thought that might be it but its not and niether is the wireless connection becuase it's still on 99%-100% weather the wireless is on or off..

for some reason the gnome-system-monitor doesn't show which process is using 100% but it does show the 100% cpu usage on the graph under resources. it shows CPU2 as having 100% and CPU 1 hovers around 68%.. This just cannot be possible! It's a fresh install.

[IMG]http://dl.dropbox.com/u/2528687/Screenshot2.png[/IMG]

---

### Post by quizno50 on 2010-08-25
What happens when you kill the process that's using so much? Find out if anything breaks; if not; we can find out what's launching it and have it stop.

---

### Post by fatriff on 2010-08-25
> **quizno50 said:**
> What happens when you kill the process that's using so much? Find out if anything breaks; if not; we can find out what's launching it and have it stop.

LOL, how exactly do you kill root??

---

### Post by quizno50 on 2010-08-25
try this:
```
sudo kill 2246
```
if you've rebooted your computer since your last screenshot of top you might need to recheck what the PID is and replace 2246 with it (it's the first number on the left)...

---

### Post by fatriff on 2010-08-25
That has stopped the 100% cpu usage.. this is what it looks like now.. 

[IMG]http://dl.dropbox.com/u/2528687/Screenshot3.png[/IMG]

Thats with firefox and the screenshot app and system monitor running and dropbox..

But if root gets launched again I will have the same issue?

---

### Post by inameiname on 2010-08-25
Yeah, I'm curious about this too. I checked mine with that 'top' command, as well as the gnome-system-monitor, and noticed both of my processors were at around 50%. I tried that killall command mention, although it said 'No such process' for me, but now both processors are below 18%. What would cause that?

---

### Post by quizno50 on 2010-08-25
> **inameiname said:**
> Yeah, I'm curious about this too. I checked mine with that 'top' command, as well as the gnome-system-monitor, and noticed both of my processors were at around 50%. I tried that killall command mention, although it said 'No such process' for me, but now both processors are below 18%. What would cause that?

The same kill command won't work twice in a row. It's a unique PID for every computer (and every program that's running). You'll have to find it by typing:
```
ps aux
```
or
```
top
```
to figure out what the PID is, then you can type
```
kill [the-pid-to-kill-here]
```

---

### Post by inameiname on 2010-08-25
Oh ok, thank you.

---

### Post by quizno50 on 2010-08-25
Well; I did a little research; and it looks like this is a bug in the sqlite libraries. Not really sure what to do about it; other than just kill the process (actually an easier way to do it is: sudo kilall backend). However I was reading here and maybe you can find something that'll help you.

[http://ubuntuforums.org/showthread.php?t=1467208](http://ubuntuforums.org/showthread.php?t=1467208)

---

### Post by inameiname on 2010-08-25
Is this that bug that occurred just before the release of Ubuntu Lucid 10.04 that would make the computer slower and slower the longer you had it on? If so, I thought they had fixed it literally right before it's release.

---

### Post by quizno50 on 2010-08-25
> Is this that bug that occurred just before the release of Ubuntu Lucid 10.04 that would make the computer slower and slower the longer you had it on? If so, I thought they had fixed it literally right before it's release.
I'm not sure, but I don't think 100% CPU usage would slow it down over time, unless it includes a memory leak... I don't see it on my install (which is pretty much fresh running on Virtual Box).

---

### Post by inameiname on 2010-08-25
Oh ok. Yeah, I think it was more a memory leak than anything as to what the bug was before.

---

### Post by fatriff on 2010-08-26
I know I cannot be the only person who is has been suffering a really slow crap system as a result of this.. it's just slow enough to make you think ubuntu is no way better than xp and you want to revert.. There must be many people going around slating ubuntu when really all that was needed was to kill the root.. Ordinary users would never realise there was an issue as this 100% cpu usage doesn't appear in gnome-system-monitor under processes.. But the graph does show the high usage.. I would think most people would probably be told it's flash player eating the cpu and to live with it!

Anyway, my system is running at the correct speed now, thanks for the solution posted :D

---

### Post by quizno50 on 2010-08-26
Glad to help... I wish we could find out a little more about *why* that was happening though so we could come up with a little more permanent solution.

---

