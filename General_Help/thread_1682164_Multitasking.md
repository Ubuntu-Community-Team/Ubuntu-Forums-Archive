---
title: "Multitasking?"
date: 2011-02-05
forum: General Help
---

### Post by yojoe on 2011-02-05
I have a Lenovo Thinkpad T60, which has ubuntu 10.10 on it, my specs were as follows; Intel Centrino Duo processor with 1 gb of ram, i just acquired a new hard drive which has 120 gb of space and windows vista, and i got another 1 gb ram stick, for some reason, i couldnt play music and play even quadrapassel at the same time without the music slowing down, even scrolling down a web page in firefox slowed the music down, ubuntu is not taking advantage of my resources or something, because with the ram upgrade in vista, i can play any game with itunes playing music in the background, and gta san andreas plays smoother than my ps2, i dont want to blame ubuntu, so i have a couple ideas, my ubuntu hd is older? maybe i can set it to take advantage of my resources. if you guys cant help im going to switch back to windows, even after everything ive done to promote linux in general, ive preached it like the word of god and i want you to help. If vista can multitask better than ubuntu, VISTA?!?!?! then im pissed, music still slows down after the ram upgrade in ubuntu

---

### Post by Perfect Storm on 2011-02-05
Thread moved.

---

### Post by yojoe on 2011-02-05
and another thing that pisses me off, is that i never get a response to my threads, and when i post a suggestion, or a fix to a problem, i get ignored, I DONT CARE WHO REPLIES, I JUST WANT A REPLY, IT DOESNT MATTER IF ITS A SOLUTION TO MY PROBLEM OR NOT, SOMEONE REPLY

---

### Post by lisati on 2011-02-05
> **yojoe said:**
> and another thing that pisses me off, is that i never get a response to my threads, and when i post a suggestion, or a fix to a problem, i get ignored, I DONT CARE WHO REPLIES, I JUST WANT A REPLY, IT DOESNT MATTER IF ITS A SOLUTION TO MY PROBLEM OR NOT, SOMEONE REPLY

Patience is a virtue. The general rule for this forum is to wait 24 hours after the last post in a thread before bumping. We're all volunteers here, living in different time zones: the person best equipped to answer your question (or at least help start the ideas flowing) might be in bed or at work.

---

### Post by sammiev on 2011-02-05
I have a few computers running 10.10 and do find myself that the multitasking isn't as good as windows but for the most part things run better as stand alone. I'm new to ubuntu but have played with it here and there for years. I for the most part and now using ubuntu as my main operating system. There is many others that maybe can help you out but I'm just stating what I have found over the years. GL :)

---

### Post by oldsoundguy on 2011-02-05
Music on playback will NOT slow down .. EVER!!
No matter the platform.
You may have it start and stop if you have buffering issues, but it will NEVER slow down.

Running some highly memory intensive game MAY cause it to stop and start if you haven't enough memory.

First thing you need to do is verify that you put the right memory into that laptop and that it is working properly.

---

### Post by Hedgehog1 on 2011-02-05
Let me be sure I understand your hardware situation:

You are swapping 2 hard drives in/out of your Thinkpad T60.  One drive has Ubuntu on it, and one drive has Vista on it. Right?

Also, you have (now) 2 gigs of ram on the Thinkpad.

Does Ubuntu recognize that there are 2 gigs of ram?  Do you have the correct video driver for you Ubuntu install on the ThinkPad?

---

### Post by asmoore82 on 2011-02-05
What type of video card does the machine have?
It's likely an nVidia or ATI card and you need to load the manufacturer's
restricted driver to get the most performance out of it.

On a side note -
To squeeze the most out of multitasking you can manually take control and
set different processes to run on certain CPU cores. There's a "miracle"
kernel patch out there that increases interactive performance by leaps
and bounds especially when the system is under a heavy load. It turns out
that all this patch really does is auto-assign and lock tasks to certain CPU cores.
There's a bit of discussion going on about whether or not this should
become the default behavior. I believe it's not optimal for server workloads.

---

### Post by psusi on 2011-02-05
> **asmoore82 said:**
> What type of video card does the machine have?
It's likely an nVidia or ATI card and you need to load the manufacturer's
restricted driver to get the most performance out of it.

Video issue is my guess too.

> **asmoore82 said:**
> On a side note -
To squeeze the most out of multitasking you can manually take control and
set different processes to run on certain CPU cores. There's a "miracle"
kernel patch out there that increases interactive performance by leaps
and bounds especially when the system is under a heavy load. It turns out
that all this patch really does is auto-assign and lock tasks to certain CPU cores.
There's a bit of discussion going on about whether or not this should
become the default behavior. I believe it's not optimal for server workloads.

That's not quite right.  What it does is group processes by what terminal they are running in and schedules them as a collective unit.  This means if you are a nut and run 64 instances of gcc in a terminal window, the scheduler gives one of them a turn, then gives some other process, like another window, a turn before giving the next one of those 64 gcc instances another turn.  This means other windows don't have to wait for all 64 instances of gcc to get a turn before they go.  Of course, nobody is crazy enough to do that, so it's kind of a pointless patch.

By the way OP, you are much more likely to get an answer when you actually ask a question instead of just rant and rave.

---

### Post by Hedgehog1 on 2011-02-05
Interest herd behavior in nerds of all kinds (I see this at the office; I am as guilty as any):

1 engineer, 1 opinion.
2 engineers, 3 opinions (one each and the consensus).
3 engineers, 7 opinions... And so on...

In this case video issue seems to be the most popular - however if the 'new' memory is not a correct match for the ThinkPad or a good match for the current 'stick', I have seen some weird things happen...  Although I would expect to see that happen in Vista, too.

:KS

---

### Post by yojoe on 2011-02-06
Im trying to play quadrapassel (tetris clone) and listen to mp3's in Rhythmbox at the same time, but the music is truly slowing down, I have a dual core processor and 2 gb of ram and Ubuntu does recognise it. It had the same problem with the factory 1 gb it had before the upgrade.

I'm sorry, I use Ubuntu predominantly and I was just mad to find that I cant listen to music while I play games, even using the scroll bar in a web browser slows it down, the computer is running fast every where else and even when Im multitasking it says im using low resources. The only reason I havent wiped vista, is because its a used hard drive from my step dad and Im helping him back up his files.

I did the whole system test and all my hardware drivers are working correctly, and I don't know how to manually set different processes to different cores

I have an ATI RADEON graphics card and I will try to download the manufacturers restricted driver and update on any change in performance.

Also Im not gonna switch back to windows, i didnt mean that

to be more exact i have an ATI mobility radeon x1300 graphics card and im having trouble finding the linux driver

---

### Post by yojoe on 2011-02-06
I found a kind of fix for this problem, i go into system> administration> system monitor, and under processes, i set rhythmbox and pulse audio priority levels up, and which ever game im running, down. but i have to do it every time i open them, Is there anyway to save priority levels for each time an application opens?

---

