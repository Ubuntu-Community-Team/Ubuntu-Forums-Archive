---
title: "What is CPU frequency scaling and why doesn't linux support it (on my pc)?"
date: 2009-12-09
forum: General Help
---

### Post by mahela007 on 2009-12-09
What is CPU frequency scaling? 
I posted another thread on my laptop's fan blowing being much hotter than it is when I run windows. I found out that this was *probably* because of the lack of something called "CPU Frequency scaling" for my celeron processor based IBM laptop (please let me know if you know if there's another reason for abnormally hot temperatures).
So, anyway, what is CPU scaling? 
and why doesn't linux support it (On that specific processor) when windows XP appears to do so... (Relax.. I'm not going to dump ubuntu just because of this and I don't want to start a windows Vs. Linux debate / argument.... but it does concern me because is might lower battery life on the laptop.

---

### Post by marshall.robert on 2009-12-09
CPU Frequency Scaling is where your processor clocks down to a slower speed to decrease power consumption. It probably does reduce heat production too.

EDIT: Found these 2 links if you want more infos.

[http://en.wikipedia.org/wiki/Dynamic_frequency_scaling](http://en.wikipedia.org/wiki/Dynamic_frequency_scaling)
[http://en.wikipedia.org/wiki/Frequency_scaling](http://en.wikipedia.org/wiki/Frequency_scaling)

---

### Post by SteveDee on 2009-12-09
> **mahela007 said:**
> ...So, anyway, what is CPU scaling? 
and why doesn't linux support it (On that specific processor) when windows XP appears to do so... 

This is not a "Linux" limitation, its just that hardware support on Ubuntu is limited. For example, Puppy Linux supports cpu scaling on a wider range of hardware.

---

### Post by Flying caveman on 2009-12-09
I've had it work on two different Celerons a Celeron M and a Socket 478 Celeron.  It just doesn't work automatically, because the CPU itself doesn't officially support it.   It was as simple as putting p4-clockmod in /etc/modules

---

### Post by wojox on 2009-12-09
[Here before you throw it out the window]("http://www.howtoforge.com/cpu_frequency_scaling_ubuntu")

;)

---

### Post by mahela007 on 2009-12-10
Like I said, I'm not going to 'throw it out the window'.. what is  	p4-clockmod?

---

### Post by mahela007 on 2009-12-11
bump..

---

### Post by mahela007 on 2009-12-11
Does this *automatically* scale the frequency?

---

### Post by audiomick on 2009-12-11
Hallo.
I had a quick look at the link.
p4_clockmode looks like a thing to monitor the frequency of the cpu and change it manually. I don't think it does anything automatically.

---

### Post by mahela007 on 2009-12-11
OK.. thanks. Well, the fix worked for me. (even if it doesn't support automatic scaling). Just out of curiosity.. does linux support automatic scaling for other (more advanced / modern) processors?

---

### Post by Hobgoblin on 2009-12-12
You might need to add the cpu frequency scaling applet to the taskbar to get on demand scaling.

---

### Post by fluffman86 on 2009-12-12
> **mahela007 said:**
> OK.. thanks. Well, the fix worked for me. (even if it doesn't support automatic scaling). Just out of curiosity.. does linux support automatic scaling for other (more advanced / modern) processors?

I wasn't aware that you could scale a celeron at all.  Apparently so.  

Anyway, to answer this last question: yes.  I have Ubuntu automatically scale my AMD Athlon 64, Pentium M (P4 Mobile/Centrino), and my Intel Atom.

---

### Post by mahela007 on 2009-12-12
Well, I've added the applet to the taskbar but I can't select the 'ondemand' option. It always goes back to 'Performance'. The only other setting I can use is powersave. It doesn't seem to support automatic scaling. How did you get it to work?

---

### Post by Hobgoblin on 2009-12-12
Did you add p4-clockmod to /etc/modules ?

---

### Post by mahela007 on 2009-12-13
Yes.. I just did. It works perfectly. I think I can see an increase in battery life.

---

### Post by Marvin666 on 2009-12-13
My last laptop had a bios option for dynamic frequency scaling. I disabled it when I looked up what it was, so I couldn't tell you about it's effects...

---

