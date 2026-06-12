---
title: "Firefox always crashes with specific flash player"
date: 2009-09-26
forum: General Help
---

### Post by J V on 2009-09-26
Turned into crisis! View page 2!

Edit: Crisis averted, resume normal lives :)

Firefox always crashes (Well, it uses so much CPU my system can't budge) when viewing gamespots videos...

Other video players are fine (Although I've only tried youtube), but gamespots videos keep crashing FF... its hard to even get an xkill out to stop it...

Known issue?

---

### Post by beastrace91 on 2009-09-26
What flash player do you have installed? 32bit Ubuntu or 64bit? Many of the open source flashplugins have issues to say the least, be sure you are using flashplugin-nonfree for the best performance.

~Jeff

---

### Post by TarasIv on 2009-09-26
I don't have this problem so I'm not sure if it's FF or your hardware. What's in your computer?

---

### Post by J V on 2009-09-26
I installed flash through ubuntu-restricted-extras, as such I presume its the nonfree 32-bit version...

Checked synaptic, flashplugin-nonfree was indeed installed with u-r-e, but I still can't find what version it is...

Whats in my computer lets see...

ubuntu 9.04...

Running in wubi (Damn legal issues)

2G ram, 2 3Ghz intel cores, GeForce 8400 GS...

---

### Post by lovinglinux on 2009-09-26
See Flash Optimization section of [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by J V on 2009-09-26
Thanks for that LL, I don't want to use mplayer though (now you ask why in horror), because in fullscreen there's no controls, you're stuck there until you go out of fullscreen...

A major bummer, unless you know a plugin that will fix that?

Otherwise thanks for the tips, I will test them shortly...

---

### Post by NoaHall on 2009-09-26
If you have the 64 bit version of Ubuntu, follow the advice from the link in my sig.

---

### Post by lovinglinux on 2009-09-26
> **J V said:**
> Thanks for that LL, I don't want to use mplayer though (now you ask why in horror), because in fullscreen there's no controls, you're stuck there until you go out of fullscreen...

A major bummer, unless you know a plugin that will fix that?

Mplayer doesn't have controls in fullscreen? Anyway, I use gecko-mediaplayer and has controls.

---

### Post by J V on 2009-09-26
After LLs tips it became possible to xkill FF within 30 seconds, not ideal...

After 64bit flash, 5% less CPU use per CPU... (at least at the part where system monitor was still functioning) but still enough to crash FF...

This is getting annoying... (Changes to ies4u: you guys yell NOOOO!)

Just gonna ask GS to do something about their players, either the most unoptimized pieces of **** I've ever seen or just plain bugged...

---

### Post by NoaHall on 2009-09-26
Maybe you have cpu scaling enabled. Try adding "cpu frequency monitor" to the toolbar and change it to full power.

---

### Post by J V on 2009-09-26
What is CPU scaling? (Sorry, that came out dumb)

Edit: Ok, I found the problem... My memory ran out... The video in particular must be over 2 gigs (2 gigs for an SD video? wtf?) and I didn't change the default 250M swap... Anyone know how to up the virtual memory in ubuntu? (On wubi btw)

---

### Post by J V on 2009-09-26
Ok, this just turned into a crisis, ergo the bump...

I resized the swap.disk to 5 gigs to give myself some space, only now my system monitor is saying:
> 0 bytes 0.0% of 0 bytesHELP!

I have no more swap, imagine the horrors that would unfold if I ran a program that needed more ram than 2 gigs!

Someone please help me, get this swap file to work please :shock:

---

### Post by J V on 2009-09-26
Logged windows for 2 reasons:
1. I don't have to worry about memory lockup...
2. I wanted to test how windows memory responds to the player...

I tested the video player and theres a big difference...

In windows, the video downloaded (about 30 megs) and sat in memory waiting... 

In ubuntu however, before the video was even halfway loaded, the entire ram + swap (2.25 gigs) was filled. How is this possible? Whatever this is is a serious flaw that would take a hella lot of work to miss...

The video in question is here: [http://www.gamespot.com/ps3/action/uncharted2amongthieves/news.html?sid=6211914&mode=previews](http://www.gamespot.com/ps3/action/uncharted2amongthieves/news.html?sid=6211914&mode=previews)

Any ideas on:
A: How a memory leak can turn 30 megs into 2 gigs in 20 seconds flat
B: How the OS can't stop the download until its got some more ram left
C: How the memory leak got there in the first place

... ies4u is lookin pretty damn attractive now :-|

---

### Post by J V on 2009-09-27
Sorry about the spam, got the swap working...

Now with my new 5 gig swap I was able to watch the video, and I had some surprising (to say the least) results...

While playing the video my ram shot from 400 megs straight up to 2 gigs, at which point things started to slow down (a lot, once again unusable), but I figured, lets just wait a moment... Once ubuntu had freed some ram, things started going smoothley again...

Later, when the video was loaded, the ram was full at 2 gigs, and the swap had 400 megs in it. When the video was loaded however, all of a sudden without any reason, the used memory droped like a rock, straight down to 1 gig, in the blink of an eye...

I believe something is wrong with the firefox/flash download protocols... I don't like flash so I have no idea what exactly happened, but I would like to be able to watch videos without the browser crapping out all the time.

Any ideas?

---

### Post by wojox on 2009-09-27
Why Wubi? What are the legal issues? You will notice problems using wubi after a while because it uses the same file fragmentation as windows. 

Split that hdd in half and dual boot. :lolflag:

---

### Post by J V on 2009-09-27
Well, I thought that the file that the partition is based on gets fragmented, but I haven't started windows in a while so thats not a problem, but isn't the file system on the inside of that file ext3? (It says so, right here)

So shoulden't that mean using the ext3 filesystem aka no fragmentation?

---

