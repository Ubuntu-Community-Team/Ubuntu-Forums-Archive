---
title: "Increase performances"
date: 2009-10-31
forum: General Help
---

### Post by gahute on 2009-10-31
Hi everyone,

I just installed my first Linux (ubuntu 9.04) a few minutes ago on my old computer (Celeron 1000MHZ with 512 Mb RAM) overwriting my Windows XP and I'd like to know if there is a list of things I could change (settings, etc.) that would improve the performances on this computer 'cause I find it a bit slow?

Should have I installed a lighter version like xubuntu?

Thanks,

---

### Post by bibekdai on 2009-10-31
i think so, use xubuntu, its a lot lighter.

---

### Post by ea1387 on 2009-10-31
My brother has Xubuntu with a Intel Pentium 4 and 256MB of RAM, and his computer is fast! Xubuntu 9.10 Karmic Koala
Running at Idle he uses 40% of Physical Ram

---

### Post by bibekdai on 2009-10-31
In the past (xubuntu 7.10 era), i have used xubuntu on a 700mhz pentium 3 with 128mb ram. its was running fine.

---

### Post by gdi2k on 2009-10-31
You may also find that adding another 512 MB RAM would be a cheap way of increasing the pace. When using the system normally, open up the System Monitor (System -> Administration) and check how much Swap is being used on the "Resources" tab. If it's a significant amount (more than a few megs) you'd likely benefit from more RAM.

---

### Post by ea1387 on 2009-10-31
C

---

### Post by gahute on 2009-10-31
Hi,

I "downgraded" to xubuntu 9.04 (you can do that directly using the terminal when ubuntu is already installed, I found that on xubuntu's website) and I'll check if it's better...

Thanks,

---

### Post by kerry_s on 2009-10-31
you can tweak gnome to be lighter then xfce4.
in gconf-editor turn on reduced resources, turn off animations. replace the heavier apps with lighter alternatives.

i'm running a full gnome 9.10 on 512mb ram, watching movies while browsing the forums. ;)

---

### Post by gahute on 2009-11-01
Hi,
 
I downgraded to xubuntu and it seems my problem is not related to my RAM (used less than 50%) but related to my Celeron 1000 MHz CPU which is oftenly (+75% of the time) running at 100%.
 
Most of your comments are talking about dual-cores, P3 and P4 processors, not Celeron. Forget it about watching a movie on my computer!!!
 
By the way, I'm new to Linux (as I wrote, I installed my first one a few hours ago only) and I'll have to google "gconf-editor" to learn about it!
 
If anybody can tell me how to lighten my xubuntu, it will be very appreciated.
 
Thanks!

---

### Post by DeMus on 2009-11-01
> **kerry_s said:**
> you can tweak gnome to be lighter then xfce4.
in gconf-editor turn on reduced resources, turn off animations. replace the heavier apps with lighter alternatives.

i'm running a full gnome 9.10 on 512mb ram, watching movies while browsing the forums. ;)

Could you please explain in detail the things you have done to improve the speed? This sounds interesting.
Thanks.

---

### Post by P4man on 2009-11-01
> **gahute said:**
> Hi,
 
I downgraded to xubuntu and it seems my problem is not related to my RAM (used less than 50%) but related to my Celeron 1000 MHz CPU which is oftenly (+75% of the time) running at 100%.
 
Most of your comments are talking about dual-cores, P3 and P4 processors, not Celeron. Forget it about watching a movie on my computer!!!
 
By the way, I'm new to Linux (as I wrote, I installed my first one a few hours ago only) and I'll have to google "gconf-editor" to learn about it!
 
If anybody can tell me how to lighten my xubuntu, it will be very appreciated.
 
Thanks!

opem a terminal and run ```
top
``` and tell us what process is hogging your cpu.

---

### Post by kerry_s on 2009-11-01
> Most of your comments are talking about dual-cores, P3 and P4 processors, not Celeron. Forget it about watching a movie on my computer!!!

i can do the same thing on my 450mhz 256mb ram laptop. so yes you can with your specs.

> I downgraded to xubuntu and it seems my problem is not related to my RAM (used less than 50%) but related to my Celeron 1000 MHz CPU which is oftenly (+75% of the time) running at 100%.


how did you determine it's running at 100% ?

---

### Post by kerry_s on 2009-11-01
> **DeMus said:**
> Could you please explain in detail the things you have done to improve the speed? This sounds interesting.
Thanks.

start here:
[http://library.gnome.org/admin/system-admin-guide/stable/performance-0.html.en](http://library.gnome.org/admin/system-admin-guide/stable/performance-0.html.en)

---

### Post by gahute on 2009-11-01
Hi kerry_s,

I saw my CPU was running at 100% in the System monitor (Moniteur système), Resources tab (onglet Resources) on CPU utilization history (Historique d'utilisation du CPU). Now I think my problem is a display lagging problem...

I'll look at your link for performances...

Thank you!

---

### Post by kerry_s on 2009-11-01
> **gahute said:**
> Hi kerry_s,

I saw my CPU was running at 100% in the System monitor (Moniteur système), Resources tab (onglet Resources) on CPU utilization history (Historique d'utilisation du CPU). Now I think my problem is a display lagging problem...

I'll look at your link for performances...

Thank you!


okay, thats what i was thinking. the system monitor is a hog & can easily drive the cpu to 100%.
try using the "top" command in a terminal instead.
under powered cpu's constantly reach 100% while working, it's perfectly normal, the only time you need to worry is if it stays that way even though you close the program that drove it up that high.

my advice just use the computer, don't worry whats happening behind the scenes, let the computer do it's job.

if you get the feeling something is wrong, just describe it as best you can & we will help point you where to look & what to look for.

for example: 
you think there is a problem with the vid, you need to give as much details about the vid card as you can, trust me theres someone else thats running that exact card & may already know the answer you need. now if you don't know the details of your vid card, we need to know that, only then can we tell you how to find them out.

---

### Post by gahute on 2009-11-01
Thanks,

I think I should finish this thread and only follow this one I started a few minutes ago 'cause I think my problem is that I don't know what I do:
[http://ubuntuforums.org/showthread.php?t=1310242](http://ubuntuforums.org/showthread.php?t=1310242)

I left the details on my hardware a few minutes ago so you can find them there. I'll try to return to the beginning and after that I'll try to look at my display problem (if it is a display problem).

How can I finish this thread?

Thanks kerry_s for your support!

---

