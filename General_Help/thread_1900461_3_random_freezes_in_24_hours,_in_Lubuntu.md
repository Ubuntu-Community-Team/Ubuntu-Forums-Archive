---
title: "3 random freezes in 24 hours, in Lubuntu"
date: 2011-12-26
forum: General Help
---

### Post by pretty_whistle on 2011-12-26
Why?  Is there a way to fix it?

I'm able to unfreeze it so that's not an issue.  I *shouldn't* have to unfreeze it though-it just shouldn't be doing it in the first place.  So this is why I've posted here-hoping to solve it so I don't have to unfreeze it anymore.

Here's how I unfreeze it if that gives a clue as to what's wrong:

-in system monitor, kill pcmanfm.
-in "run" field, type this:

pcmanfm --desktop --profile=lubuntu

---

### Post by pretty_whistle on 2011-12-26
If it helps to know this, Firefox was open in each case of freezing.  Other windows I had open weren't the same every time though.

I have Firefox 8.
The OS is 32bit.

---

### Post by 2F4U on 2011-12-26
Since you provide almost no information, it will be difficult to help you. As a minimum, you should provide the following information:
- hardware
- graphics card and driver
- any pattern you recognize as a possible reason for the freezes
- is this an upgraded system or a fresh install
- did it happen from the beginning or started just recently

Did you look into the system log files when the freeze happens? This shouldn't be a problem since it seems that you can still operate the machine during the freeze.

---

### Post by 2F4U on 2011-12-26
Any specific websites, for example with flash on it?

---

### Post by pretty_whistle on 2011-12-26
Thanks for replying. I'll try to answer you-I'm a noob so please bear with me.   Here goes....

1. Hardware, graphics card, etc.  Where do I find system info?
2. Any pattern noticed?  Just that Firefox is open at the time.
3. Upgraded or fresh install?  It was a fresh install.
4. Happen from the beginning or started just recently?  About 24 hours I ago I installed Lubuntu, and it started then.
5. Did I look at system logs?  No, don't know where to find them.

---

### Post by pretty_whistle on 2011-12-26
> **2F4U said:**
> Any specific websites, for example with flash on it?
Nope.  I was on here most of that time.

---

### Post by pretty_whistle on 2011-12-26
Ok.  Here's a bit I was able to dredge up:

HP Compaq Presario CQ50 Laptop
160GB HDD
158GB free space
Dual core
nVidia adapters, GeForce 8200

---

### Post by pretty_whistle on 2011-12-26
I just edited my last post with more specs I could find.

---

### Post by pretty_whistle on 2011-12-26
Anyone?

---

### Post by MG&amp;TL on 2011-12-26
when you say "freeze"-can you describe a bit more explicitly? Does Ctrl-Alt-F1 work?

---

### Post by pretty_whistle on 2011-12-26
> **MG&TL said:**
> when you say "freeze"-can you describe a bit more explicitly? Does Ctrl-Alt-F1 work?
What I mean by freeze is I can't click on anything on the desktop.  I can move the cursor fine though.  The browser and other windows I have open are the same way-I can click but nothing responds.

As to CTRL+ALT+F1, I didn't try that.

---

### Post by pretty_whistle on 2011-12-26
Add this to my desktop messing up:

> It turns blank (the desktop, I mean).  Icons are all gone. This has been like the 4th time today.

Perhaps pcmanfm is messing up.

This is probably caused by whatever has been freezing it.

---

### Post by MG&amp;TL on 2011-12-27
Sorry, no clue. If you can still move your mouse, what effect does Alt-TAB have?

(I'm thinking some window has got 'stuck' at the top level and won't come down again) 

Have fun! :)

---

### Post by Elfy on 2011-12-27
I'd be inclined to running a terminal up in the corner somewhere so you can see it - run top in it.

When it freezes have a look see if that shows anything taking lots of cpu.

---

### Post by pretty_whistle on 2011-12-27
> **forestpiskie said:**
> I'd be inclined to running a terminal up in the corner somewhere so you can see it - run top in it.

When it freezes have a look see if that shows anything taking lots of cpu.
That's what I was thinking.  

Firefox was peaking at times about 90% !

What to do about that though...... I dont know.

---

### Post by Elfy on 2011-12-28
Cut down on addons - try a different browser - what memory do you have?

```
free -m
```

---

### Post by pretty_whistle on 2011-12-28
> **forestpiskie said:**
> Cut down on addons - try a different browser - what memory do you have?

```
free -m
```
Here's what I got from free -m:

nutin@nutin:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1758       1172        586          0        115        539
-/+ buffers/cache:        517       1240
Swap:         1788          0       1788

I have 2 GB ram.

---

### Post by pretty_whistle on 2011-12-28
I'm not using that browser anymore and because of it CPU isn't getting eaten up.
The problems I had have stopped.

Thanx for helping out!  :D  :D

---

