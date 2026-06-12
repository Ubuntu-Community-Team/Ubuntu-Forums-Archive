---
title: "Quick Boot Up in 10.4 - reminds me of Vista"
date: 2010-04-25
forum: General Help
---

### Post by JohnH on 2010-04-25
Hi all,

Not wanting to wave a red flag at the Ubuntu bull, but I'm running the 10.4 64bit RC. Sure it boots up to the desktop quickly but my four CPUs run at 100% for around 30 seconds after the desk top appears.

Now this is a bit like Vista who made claims about quick boot ups to the desktop. Unfortunately you had to wait forever before the system settled down enough to start work.

Is Ubuntu picking up bad habits from the the master of bad habits? Or am I dreaming?

Over to you cafe drinkers.

---

### Post by tom66 on 2010-04-25
That's probably a bug - my CPU goes idle a couple seconds after boot completes. I'm running 10.04. As soon as the panels appear I can launch any application.

---

### Post by wilee-nilee on 2010-04-25
> **tom66 said:**
> That's probably a bug - my CPU goes idle a couple seconds after boot completes. I'm running 10.04. As soon as the panels appear I can launch any application.

Same here, @OP you wont get much sympathy here comparing the OS, even though many of us run multiple OS.

---

### Post by NightwishFan on 2010-04-25
I get a bit of high cpu usage here on Intregrated Intel GPU until the desktop loads. (My mouse moves choppy) It might have something to do with Xorg having too little priority when under heavy I/O.

When it is booted: I catch watch a 1080p video while converting a lot of audio into vorbis, chatting, web browsing, and reading apt database/install ing updates (this managed to all seem to happen at once). I have no lag with my mouse then, and not even any frame drops on the video.

As a note I use the anticipatory scheduler. I might try to renice xorg to -1 and see how it goes.

EDIT: You can improve desktop login time by installing the preload daemon, but being on a laptop I do not want my disk working any more than it needs to. [Click To Install Preload]("apt://preload")

---

### Post by Al Fairclough on 2010-04-25
I am afraid that Win 7 and 10.04 are nowhere in the same league. Whereas Win 7 is fast for a MS operating system, 10.04 simply schools it.

---

### Post by NightwishFan on 2010-04-25
Update: Not sure how to get xorg to start as nice -1 when I log in... However the gnome shell is much smoother if I nice xorg after log in.

---

### Post by Linuxforall on 2010-04-25
My 8 cores in the dual XEON hardly touch around 30% and that too on few of the cores.

---

### Post by kenweill on 2010-04-25
Same here. I got 100% cpu usage on my dual core machine. Though, its alternating. When cpu1 is 100%, cpu2 is about 50%. When cpu2 goes up to 100%, my cpu1 gets about 50% usage. And this happens even though, im not doing anything. Even my computer is idle. nvidia non-free is installed in my machine, with effects disabled.

---

### Post by NightwishFan on 2010-04-25
That sounds like a glitch refer to top or gnome-system-monitor (viewing all processes) to see what is using the cpu. If it is xorg, you might have installed using a CD that was not burned correctly,

---

### Post by kenweill on 2010-04-25
> **NightwishFan said:**
> That sounds like a glitch refer to top or gnome-system-monitor (viewing all processes) to see what is using the cpu. If it is xorg, you might have installed using a CD that was not burned correctly,

i did that. view the processes but nothing. 0%. except for the system monitor that goes up to something about 16% cpu usage. nothing else in the processes is above 16%, ordered by cpu usage.

---

### Post by NightwishFan on 2010-04-25
Top in the terminal is easier to see, it is sorted by cpu usage by default. I am willing to bet the culprit is either xorg or npviewer.bin
```
top
```

---

### Post by kmsalex on 2010-04-25
i've always fond ubuntu to idela higher then windows (vista or 7). in windows if i only open task manager and don't move the mouse it will go down to 0% on both cores. but in ubnutu if i do the same thing the 2 cores will jump in between 5% and 15%.

---

### Post by NightwishFan on 2010-04-25
No, Linux probably idles around 0-1% the system monitor itself is what makes it jump. It has to render those charts using SVG images (perhaps cairo?). That is why.

---

### Post by Xbehave on 2010-04-25
bootchart or it didn't happen! but seriously it sounds like a bug a quick look at your bootchart should give enough info to help you.

---

### Post by cariboo on 2010-04-25
This is more of a General Help question, than a Cafe thread. Moved.

---

### Post by mc4man on 2010-04-25
> Sure it boots up to the desktop quickly but my four CPUs run at 100% for around 30 seconds after the desk top appears.


*Only in cases where frequency scaling is applicable* - then the default behavior is to start in performance mode for 60 sec.'s, then switch to ondemand.

The 60 sec's can be adjusted in /etc/init.d/ondemand, though there is no good reason to do so.. 
(though for my hardware - core2duo laptop, lowering the up_threshold has made a significant difference in overall performance in a positive sense

---

